---
stoplight-id: asj3rbo9v9cvf
---

# Spend

Spend can be quantified in two ways:

1. **Booking owner** — The `CustomerId` associated with bookings. Note that many POS bookings are not assigned a booking owner.
2. **Booking signed waivers** — This method enables you to associate specific customers with tickets and reference the `TicketId` from the Revenue endpoint to identify the spend for each ticket.

If you do not wish to allocate spend to minors, you need to add logic that references the `ParentSignedWaiverId` of the minor and allocates the spend appropriately.
