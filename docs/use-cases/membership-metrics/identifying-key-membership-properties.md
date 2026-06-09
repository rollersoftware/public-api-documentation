---
stoplight-id: ff5bd9ebd202e
---

# Identifying Key Membership Properties

## Membership properties

- **Membership status** at a booking level can be identified from the `meta` property in the [**Get bookings**](../../../reference/data-api.yaml#/paths/~1data~1bookingitems/get) endpoint response. The attribute of this property is `MembershipStatus` and contains one of the following values: `Active` (Current), `Pending` (Pending Activation), `Suspended` (Declined Payment), `Deactivated` (Terminated), `PendingDeactivation` (Pending Cancellation), or `PendingPause` (Pending Pause).
- **Membership status from a date range** is available via the [**Membership statuses**](../../../reference/data-api.yaml#/paths/~1data~1membershipstatuses/get) endpoint, which provides a data log of historical membership status changes. The **cancellation or expiry date** is retrieved via the same endpoint.
- **Membership start date** can be identified via the `bookingDate` property in the [**Get bookings**](../../../reference/data-api.yaml#/paths/~1data~1bookingitems/get) endpoint, and provides the date the membership was valid from.
- **Membership billing cycle** can be identified from the [**Get tickets**](../../../reference/data-api.yaml#/paths/~1data~1tickets/get) endpoint via the `recurringPaymentFrequency` property. This may return the values `Daily`, `Weekly`, `Monthly`, or `Yearly`. The **billing anniversary date** is the `bookingDate` returned via [**Get bookings**](../../../reference/data-api.yaml#/paths/~1data~1bookingitems/get).
- **Recurring membership payments** can be identified via the `transactionLocation` property found via the [**Get revenue entries**](../../../reference/data-api.yaml#/paths/~1reporting~1revenue-entries/get) endpoint, when the value is equal to `recurringPayment`.
  - Filter only for where the `entryType` property is `Transaction`.
  - The `fundsReceived` property is the **amount of the recurring payment**.

## Membership redemptions

Membership redemptions are retrieved via the [**Membership redemptions**](../../../reference/data-api.yaml#/paths/~1data~1membershipredemptions/get) endpoint.

Redemptions for memberships are triggered in two ways:

- When the membership ID (`ticketId`) is used as a discount code applied to another booking, typically to purchase another product (most common).
- When the membership booking item is "checked in" at POS (by clicking the checkbox), which also produces a record in the Attendances endpoint.
