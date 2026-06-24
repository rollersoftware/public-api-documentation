---
stoplight-id: z98vm2xgkep3p
---

# Booking Limitations

When creating bookings, there are limits that govern the total number of allowed items and tickets on a single booking.

The maximum booking limitations are:

- No more than 50 different booking items (line items).
- No more than 4,000 total quantity of items/tickets.
- No more than 2,000 total quantity of packages (the package "container" itself counts as an item).
- No more than 500 recurring sessions.

> #### Group passes
> Products configured with group pass settings generate several items/tickets for a single product.
>
> For example, a `Family of 4 Jump Package` contains:
> - `1` x `90 Minute Jump` (session product configured with a **group size** of `4`)
> - `2` x `Jump Socks` (stock product)
>
> A booking with `3` x `Family of 4 Jump Package` products would therefore contain:
> - `3` x (`1` x `4` + `2` + `1`) = `21` items/tickets

Where larger bookings are required beyond these limits, we recommend creating several bookings instead.

> Attempting to [**create a booking**](https://docs.roller.app/docs/api/rest/operations/create-a-booking) beyond these limits returns a `409 Conflict` describing the error.
