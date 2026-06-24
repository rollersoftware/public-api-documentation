---
stoplight-id: ff5bd9ebd202e
---

# Identifying Key Membership Properties

## Membership properties

- **Membership status** at a booking level can be identified from the `meta` property in the [**Get bookings**](https://docs.roller.app/docs/api/reporting/operations/get-bookings) endpoint response. The attribute of this property is `MembershipStatus` and contains one of the following values: `Active` (Current), `Pending` (Pending Activation), `Suspended` (Declined Payment), `Deactivated` (Terminated), `PendingDeactivation` (Pending Cancellation), or `PendingPause` (Pending Pause).
- **Membership status from a date range** is available via the [**Membership statuses**](https://docs.roller.app/docs/api/reporting/operations/get-membership-statuses) endpoint, which provides a data log of historical membership status changes. The **cancellation or expiry date** is retrieved via the same endpoint.
- **Membership start date** can be identified via the `bookingDate` property in the [**Get bookings**](https://docs.roller.app/docs/api/reporting/operations/get-bookings) endpoint, and provides the date the membership was valid from.
- **Membership billing cycle** can be identified from the [**Get tickets**](https://docs.roller.app/docs/api/reporting/operations/get-tickets) endpoint via the `recurringPaymentFrequency` property. This may return the values `Daily`, `Weekly`, `Monthly`, or `Yearly`. The **billing anniversary date** is the `bookingDate` returned via [**Get bookings**](https://docs.roller.app/docs/api/reporting/operations/get-bookings).
- **Recurring membership payments** can be identified via the `transactionLocation` property found via the [**Get revenue entries**](https://docs.roller.app/docs/api/reporting/operations/get-revenue-entries) endpoint, when the value is equal to `recurringPayment`.
  - Filter only for where the `entryType` property is `Transaction`.
  - The `fundsReceived` property is the **amount of the recurring payment**.

## Membership redemptions

Membership redemptions are retrieved via the [**Membership redemptions**](https://docs.roller.app/docs/api/reporting/operations/get-membership-redemptions) endpoint.

Redemptions for memberships are triggered in two ways:

- When the membership ID (`ticketId`) is used as a discount code applied to another booking, typically to purchase another product (most common).
- When the membership booking item is "checked in" at POS (by clicking the checkbox), which also produces a record in the Attendances endpoint.
