---
stoplight-id: pcllb0ofwiahw
---

# Managing Refunds

Processing a refund via the API only adds a record of the transaction in ROLLER — it does not actually refund the guest. The refund must still be actioned separately. If the original payment was taken via:

- **ROLLER Payments**: It must be refunded via Venue Manager. See the help center article [**here**](https://support.roller.software/hc/en-us/articles/115001725434-Refund-a-booking-from-the-Venue-Manager).
- **An external payment processor**: It must be refunded via that payment gateway's portal.

Bookings can be refunded via the API in two ways:

1. Using the [**Payments**](../reference/rest-api.yaml#/paths/~1bookings~1{uniqueId}~1payments/post) endpoint.
2. Using the [**Cancel a booking**](../reference/rest-api.yaml#/paths/~1bookings~1{uniqueId}~1cancel/post) endpoint.

<!-- theme: warning -->
> #### When processing refunds via the API
> - Ensure you do not refund more than the amount already paid on the booking.
> - Refunding payments made via ROLLER Payments is currently unsupported.

## Examples

### Example 1

1. A guest books and pays $30 via your external payment system, or via ROLLER Payments through the API.
2. You create the booking via the API and include the payment transaction details.
3. Later, the booking is cancelled:
   1. You refund the $30 externally.
   2. You then cancel the booking via [**Cancel a booking**](../reference/rest-api.yaml#/paths/~1bookings~1{uniqueId}~1cancel/post) and include the refund transaction details, which logs the refund in ROLLER.

### Example 2

1. A guest books and pays $20 through a ROLLER Checkout (ROLLER Payments).
2. Later, you add a $10 upsell via the API and collect that $10 using your external payment system.
3. Later, a full refund is requested:
   1. The $20 refund must be processed manually within ROLLER (as it was taken via ROLLER Payments).
   2. The $10 refund can be refunded either manually or via the API, as long as it is also refunded via the external payment gateway's portal.
