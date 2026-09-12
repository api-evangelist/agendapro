---
name: agendapro-book-appointment
description: Find an available slot for a service at an AgendaPro merchant location and create a booking for a client, honoring merchant policy and the absence of idempotency protection.
api: AgendaPro Connect v3
base_url: https://connect.agendapro.com
operations:
  - listLocations
  - listServices
  - listAvailableSlots
  - quickSearchClients
  - createClient
  - createBooking
  - getBooking
scopes:
  - locations:read
  - services:read
  - bookings:read
  - clients:read
  - clients:write
  - bookings:write
generated: '2026-09-12'
method: generated
source: openapi/agendapro-connect-v3-openapi.yml + https://developers.agendapro.com/docs/getting-started
---

# Book an appointment

Turn "book me a haircut next Tuesday" into a real AgendaPro booking.

Authenticate every call with `Authorization: Bearer <apk_live_...>`. The key is bound to one
company; there is no `company_id` parameter and you cannot address another merchant.

## Steps

1. **Resolve the location.** `listLocations` (`GET /v3/locations`). Paginated —
   `page` / `per_page` (default 30, max 100). Take the `id`.
2. **Resolve the service.** `listServices` (`GET /v3/services`), then `getService`
   (`GET /v3/services/{id}`) if you need duration or price. Services are read-only.
3. **Find real availability.** `listAvailableSlots` (`GET /v3/available_slots`).
   `location_id` and `start_date` are **required**. The response is a `slots` array plus a
   `metadata` object. Never guess a time — this is the only operation that tells you what the
   merchant will actually accept, and there is no dry-run on `createBooking`.
4. **Find or create the client.** Try `quickSearchClients`
   (`GET /v3/clients/quick-search?q=...`) first — it matches name, email, phone, identification
   number and record number, and exists precisely to stop you creating duplicates. Only if it
   returns nothing, call `createClient` (`POST /v3/clients`). At least one of `last_name`,
   `email` or `phone` is required; `phone` must be E.164; `email` is lowercased on write.
5. **Create the booking.** `createBooking` (`POST /v3/bookings`) → `201`.
6. **Confirm.** `getBooking` (`GET /v3/bookings/{id}`).

## Rules that will bite you

- **There is no idempotency key.** `POST /v3/bookings` has no replay protection. If the call
  times out, do **not** blind-retry — call `listBookings` with `client_id` (and a
  `start_date`/`end_date` window) and check whether the booking already landed. A blind retry
  creates a second appointment for a real person.
- **`listBookings` requires an entity filter.** At least one of `client_id`, `location_id`,
  `service_id` or `service_provider_id`. Dates alone return `400 required / params`.
- **Notifications are suppressed.** Bookings created through the public API do not send the
  merchant's email, SMS or WhatsApp reminders. If the customer needs to hear about it, that is
  your job. `creative_source` is forced to `connect`.
- **Back off on 429.** Two limits apply per company: 70 requests/minute
  (`burst_limit_exceeded`) and 10,000/day (`daily_quota_exceeded`). Read `Retry-After` and the
  `X-RateLimit-Burst-Remaining` / `X-RateLimit-Remaining` headers.

## Errors

Envelope is `{ "error": ..., "detail": ... }` — not RFC 9457.

| Status | error | detail | Do |
| --- | --- | --- | --- |
| 400 | `required` | `params` | Add an entity filter to `listBookings`. |
| 401 | `unauthorized` | `invalid_api_key` | Re-issue the key. Do not retry. |
| 401 | `unauthorized` | `api_config_inactive` | Merchant must re-enable API access (Pro plan). Do not retry. |
| 403 | `forbidden` | `scope_denied` | The key lacks the scope. Do not retry. |
| 404 | `location_not_found` | | The location is not on this company. |
| 429 | `rate_limited` | `burst_limit_exceeded` / `daily_quota_exceeded` | Honor `Retry-After`. |
| 502 | `upstream_unavailable` | | Transient — exponential backoff. |

Full catalogue: `errors/agendapro-problem-types.yml`.
