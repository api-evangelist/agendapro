---
name: agendapro-cart-checkout
description: Build an AgendaPro cart, raise an online payment request, hand the customer a checkout URL, and release reserved bookings correctly if they abandon.
api: AgendaPro Connect v3
base_url: https://connect.agendapro.com
operations:
  - createCart
  - getCart
  - updateCart
  - createPaymentRequest
  - cancelPaymentRequest
  - listSales
  - getSale
scopes:
  - carts:write
  - payment_requests:write
  - sales:read
generated: '2026-09-12'
method: generated
source: https://developers.agendapro.com/reference/createpaymentrequest + https://developers.agendapro.com/reference/cancelpaymentrequest
---

# Take an online payment

This flow moves real money and reserves real appointment time. Two clocks run against you.

## Steps

1. **Create the cart.** `createCart` (`POST /v3/carts`) → `201`. Add service and/or product
   items. **A cart expires 24 hours after creation** — after that every call returns
   `422 cart_expired` and you must build a new one. There is no delete operation.
2. **Amend if needed.** `updateCart` (`PATCH /v3/carts/{id}`) or read it back with `getCart`.
3. **Raise the payment request.** `createPaymentRequest`
   (`POST /v3/carts/{id}/payment_requests`) → `201`. The checkout URL comes back in
   `params.checkout_url`. Give that URL to the customer; the channel is always `online` and
   cannot be chosen. The request always covers the **full** cart total — there is no partial
   payment.
4. **Watch the second clock.** If the cart holds service items with on-demand booking
   instances, the bookings are **created and reserved at this point** and `params.expires_at`
   is set roughly **15 minutes** out. Miss it and the payment request expires and the
   reservations are released automatically.
5. **Confirm.** Subscribe to the `payment_request.paid` webhook, or poll `listSales` /
   `getSale`. Sales are read-only here.

## If the customer abandons

Call `cancelPaymentRequest` (`PATCH /v3/payment_requests/{id}/cancel`). This releases the
reserved bookings **immediately** instead of holding the merchant's calendar hostage for the
full 15 minutes. Do this whenever the customer backs out or the cart changes — it is the
single most considerate thing an agent can do to a merchant's day.

Only a `pending` request can be cancelled; anything else returns
`422 payment_request_invalid_status`.

## Rules that will bite you

- **Creating a new payment request cancels the previous pending one.** That is a documented
  side effect, not a no-op. Combined with the absence of any idempotency key, a blind retry of
  `createPaymentRequest` after a timeout silently invalidates a checkout URL the customer may
  already be looking at. Call `getCart` and inspect the existing request first.
- **There is no refund, void or reversal operation.** Once a sale completes, money is moved
  back inside the AgendaPro product, not over this API. Never promise a customer a refund
  through the integration.
- **Online payments must be enabled for the merchant.** Otherwise
  `422 company_payments_disabled`. Terminal for this cart.
- **Cart and payment errors are not uniform.** These endpoints proxy an internal
  platform-sales service whose validation errors pass through with legacy single-key codes —
  `item_invalid_type`, `invalid_start_time`, `creative_source_not_public`,
  `booking_already_sold` — and do **not** follow the `{error, detail}` envelope. Parse
  defensively.

## Errors

| Status | error | Notes |
| --- | --- | --- |
| 403 | `forbidden` / `scope_denied` | needs `carts:write` or `payment_requests:write` |
| 404 | `cart_not_found`, `payment_request_not_found` | |
| 422 | `cart_expired` | older than 24h — build a new cart |
| 422 | `cart_paid` | the cart already has a paid sale |
| 422 | `company_payments_disabled` | terminal |
| 422 | `payment_request_invalid_status` | not `pending` |
| 400/422 | *(upstream passthrough)* | legacy single-key codes |
| 429 | `rate_limited` | honor `Retry-After` |
