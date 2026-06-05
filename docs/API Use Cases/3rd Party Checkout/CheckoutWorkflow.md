---
stoplight-id: 15x291npk7c3d
---

# Checkout Workflow

The recommended workflow for an external checkout is as follows:

1. [**Product Availability**](https://docs.roller.app/docs/rest-api/efb9788ea3808) should be called for the date/s the customer has selected on the checkout. Specific product/s or product categories can be specified in the call. This will provide the available capacities remaining for the given date along with relevant product, price and tax information required for display on the checkout. Additional product parameters can be accessed on the [**Product Detail**](https://docs.roller.app/docs/rest-api/4036b3635053a) endpoint if required (these should be cached and not called each time as they will change infrequently).
2. The customer adds available products to their cart. Products from multiple dates and products can be booked in a single booking.
3. When the customer proceeds to the next stage of the checkout, the required customer information (name, email and phone) should be collected.
4. At this stage, a [**Capacity Reservation**](https://docs.roller.app/docs/rest-api/d88af46de3b8c) should be created for the items the customer has selected. Capacity reservations will be valid for 10 minutes.
5. If the customer adjusts their order or abandons the checkout, the capacity reservation should be [**deleted**](https://docs.roller.app/docs/rest-api/pj5d0034eqv68) so that capacity may be booked by others, or so that a new capacity reservation can be created for the updated order.
6. Payment should be taken. Please see [**here**](https://docs.roller.app/docs/roller-payments/e4x9qrxpg5iwd) for payment processing using ROLLER Payments. If using payment processing external of ROLLER, only a record of a successful payment can be created in ROLLER.
7. Once payment is successful, the booking should be created along with the associated payment and customer information using the [**Create Booking**](https://docs.roller.app/docs/rest-api/5703708522c6b) endpoint.