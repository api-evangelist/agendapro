---
name: agendapro-modify-or-cancel-booking
description: Reschedule or cancel an existing AgendaPro booking, correctly interpreting the merchant's customer policy so the agent never retries a refusal it cannot win.
api: AgendaPro Connect v3
base_url: https://connect.agendapro.com
operations:
  - listBookings
  - getBooking
  - listAvailableSlots
  - updateBooking
  - cancelBooking
scopes:
  - bookings:read
  - bookings:write
generated: '2026-09-12'
method: generated
source: https://developers.agendapro.com/reference/updatebooking + https://developers.agendapro.com/reference/cancelbooking
---

# Modify or cancel a booking

This is the reversal path for `createBooking`, and it is **conditional**. Whether it works is
decided by merchant configuration you cannot read through the API.

## Steps

1. **Locate the booking.** `listBookings` (`GET /v3/bookings`) with at least one entity filter,
   or `getBooking` (`GET /v3/bookings/{id}`) if you already hold the id.
2. **To reschedule:** confirm the new time with `listAvailableSlots` first, then
   `updateBooking` (`PATCH /v3/bookings/{id}`). PATCH is a **partial** update — send only the
   fields you are changing. There is no PUT.
3. **To cancel:** `cancelBooking` (`PATCH /v3/bookings/{id}/cancel`) → `204 No Content`.

## The merchant policy gate — read this before you retry anything

Both operations are validated against the merchant's customer policy *before* being applied.
A refusal comes back as `422 restricted` and the `detail` field names the rule that tripped:

| detail | Meaning | Retryable? |
| --- | --- | --- |
| `can_edit` | The merchant disabled edits through the customer flow. | **No.** Terminal. |
| `can_cancel` | The merchant disabled cancellations through the customer flow. | **No.** Terminal. |
| `before_edit_booking` | The booking is inside the merchant's pre-start lock window. | **No.** Terminal — and it only gets later. |
| `max_changes` | The booking hit the merchant's maximum number of changes. | **No.** Terminal. |

Surface all four to the end user as *"the merchant does not allow this change"* — that is the
provider's own instruction. Retrying burns rate-limit budget and will never succeed.

**The lock window has no published length.** `before_edit_booking` is real, but the merchant
sets it in Configuraciones > Sitio web > Edición y cancelación de reservas en línea and the API
does not expose it. You cannot compute in advance whether a cancellation will be accepted; you
can only attempt it and read the refusal. Tell the user that, rather than promising a window.

**Every edit consumes a change.** `max_changes` counts updates, so reversing your own mistake
costs the customer one of their allowed changes. Confirm before you PATCH.

## Errors

| Status | error | detail |
| --- | --- | --- |
| 401 | `unauthorized` | `invalid_api_key`, `api_config_inactive` |
| 403 | `forbidden` | `scope_denied` — needs `bookings:write` |
| 404 | `not_found` | `booking` |
| 422 | `restricted` | `can_edit`, `can_cancel`, `before_edit_booking`, `max_changes` |
| 429 | `rate_limited` | `burst_limit_exceeded`, `daily_quota_exceeded` |
| 502 | `upstream_unavailable` | |
