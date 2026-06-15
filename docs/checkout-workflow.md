---
stoplight-id: 15x291npk7c3d
---

# Checkout Workflow

The recommended workflow for an external checkout is as follows:

1. Call [**Product availability**](../reference/rest-api.yaml/paths/~1product-availability/get) for the date(s) the customer has selected on the checkout. You can specify particular products or product categories in the call. This returns the available capacity remaining for the given date, along with the relevant product, price, and tax information required for display on the checkout. Additional product parameters can be accessed on the [**Product detail**](../reference/rest-api.yaml/paths/~1products/get) endpoint if required. Cache these rather than calling them each time, as they change infrequently.
2. The customer adds available products to their cart. Products from multiple dates can be booked in a single booking.
3. When the customer proceeds to the next stage of the checkout, collect the required customer information (name, email, and phone).
4. At this stage, create a [**Capacity reservation**](../reference/rest-api.yaml/paths/~1capacity-reservation/post) for the items the customer has selected. Capacity reservations are valid for 10 minutes.
5. If the customer adjusts their order or abandons the checkout, [**delete**](../reference/rest-api.yaml/paths/~1capacity-reservation~1{uniqueId}/delete) the capacity reservation so that the capacity can be booked by others, or so that a new capacity reservation can be created for the updated order.
6. Take payment. See [**ROLLER Payments**](roller-payments-workflow.md) for payment processing using ROLLER Payments. If you process payments outside of ROLLER, only a record of a successful payment can be created in ROLLER.
7. Once payment is successful, create the booking along with the associated payment and customer information using the [**Create booking**](../reference/rest-api.yaml/paths/~1bookings/post) endpoint.
