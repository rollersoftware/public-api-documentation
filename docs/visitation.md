---
stoplight-id: ochlprd3ppcj4
---

# Visitation

Each `BookingSignedWaiver` can be considered a visit.

The [**Tickets**](../reference/data-api.yaml#/paths/~1data~1tickets/get) endpoint response includes `ProductId`, which can be used to quantify the number of visits for a specific product if required. You can do this by associating the `BookingSignedWaivers` with tickets that have a particular `ProductId`.

The quantity of bookings a customer holds as the booking owner can also be used. However, the booking owner is frequently not a participant (ticket holder) and would therefore not be associated with a `BookingSignedWaiver`.
