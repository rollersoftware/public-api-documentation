---
stoplight-id: 9bui4ynpb1etn
---

# Associating Customers to Bookings

Customers can be associated with bookings in two ways:

1. As the booking owner (there can only be one per booking).
2. By having their signed waiver record attached to a ticket within the booking (one unique signed waiver record is attached to each ticket).

Within the [**Booking items**](../reference/data-api.yaml#/paths/~1data~1bookingitems/get) endpoint, there is a `BookingCustomerId` field, which is the `CustomerId` of the booking owner. If a booking owner is assigned, then the spend on that booking can be attributed directly to that customer.

Booking owners are assigned for every booking created via the online checkout. However, they are frequently not assigned by operators in POS bookings.

Where venues require waivers, a waiver must be associated with a ticket, and booking signed waivers enable this customer association. A booking signed waiver is a record of a waiver being linked to a ticket within the booking. The [**Booking signed waivers**](../reference/data-api.yaml#/paths/~1data~1bookingsignedwaivers/get) endpoint returns three key identifiers:

1. `BookingReference` — also present in the Booking items endpoint response.
2. `TicketId` — also present in the Tickets endpoint response.
3. `SignedWaiverId` — also present in the Signed waivers endpoint response.

These identifiers enable you to associate specific customers with bookings and individual tickets.
