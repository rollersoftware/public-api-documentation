---
stoplight-id: z98vm2xgkep3p
---

# Booking Limitations

When creating bookings there are limits that govern the total number of allowed items/tickets on a single booking. 

Maximum booking limitations are:

- No more than 50 different booking items (line items)
- No more than 4,000 total quantity of items/tickets
- No more than 2,000 total quantity of packages (the package 'container' itself counts as an item)
- No more than 500 recurring sessions

> #### Group Passes
> Note that products configured with group pass settings will generate several items/tickets for a single product. 
>
> For example:
> * `Family of 4 Jump Package` contains:
>   * `1` x `90 Minute Jump` (session product configured with a **group size** of `4`)
>   * `2` x `Jump Socks` (stock product)
> * Therefore a booking with `3` x `Family of 4 Jump Package` products would contain:
>   * `3` x (`1` x `4` + `2` + `1`) = `21` items/tickets

Where larger bookings are required beyond these limits, we recommend creating several bookings instead. 

> Attempting to use [**create a booking**](https://docs.roller.app/docs/rest-api/5703708522c6b) beyond these limits will return a **409 Conflict** describing the error.