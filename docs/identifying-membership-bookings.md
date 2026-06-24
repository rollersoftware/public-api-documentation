---
stoplight-id: 31b6e4c55b4f4
---

# Identifying Membership Bookings

When retrieving memberships and associated data, it helps to understand how memberships are structured:

- Memberships are considered a type of **product**.
- A membership always belongs to a booking.
- A booking can contain several memberships.
- Each membership has a unique booking item record, with a quantity of 1.
- A booking always has only one "booking holder" (that is, an attached guest record).
- A booking always has only one stored card token, used to charge recurring payments for all memberships on the booking.
- Individual memberships on bookings may have ticket names stored against them, and waivers attached.

To identify bookings containing memberships:

1. Use the [**Get products**](https://docs.roller.app/docs/api/reporting/operations/get-products) endpoint to retrieve all `productId`s for your products (including memberships). Using the returned `productSubType` property and our [**Product Type Mapping**](product-type-mapping.md) resource, you can determine which `productId`s are memberships.
2. Use this `productId` property in the response from [**Get bookings**](https://docs.roller.app/docs/api/reporting/operations/get-bookings) or [**Get booking**](https://docs.roller.app/docs/api/rest/operations/get-booking-detail) to identify memberships on bookings.
