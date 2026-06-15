---
stoplight-id: iglgjf34psufs
---

# Changelog

All notable changes to ROLLER's public APIs are documented here.

Releases are grouped by month and listed most-recent-first. Within each release, changes are grouped by type:

- **Added** — New endpoints, webhooks, properties, or capabilities.
- **Changed** — Changes to naming, behaviour, performance, or documentation.
- **Deprecated** — Features still available but scheduled for removal.
- **Fixed** — Corrections that align actual behaviour with expected behaviour.

Each entry notes the affected API (Reporting API or REST API) and links to the relevant reference.

## 2026-06

### Added

- New [**Get NetSuite settings**](../reference/rest-api.yaml/paths/~1netsuite-settings/get) and [**Update NetSuite settings**](../reference/rest-api.yaml/paths/~1netsuite-settings/put) endpoints to manage NetSuite integration settings for a venue: `locationId` (maps the ROLLER venue to a NetSuite location for consolidated reporting) and `exportId` (prefix for NetSuite export row IDs) (REST API).
- [**Get product availability calendar**](../reference/rest-api.yaml/paths/~1product-availability~1calendar/get) endpoint (`GET /product-availability/calendar`) to retrieve the availability status for each day in a given month for a single product. Designed for date picker and calendar UIs in third-party checkouts (REST API).
- **Booking metadata** — User-defined key-value pairs can now be stored against bookings. The `metadata` property is supported on [**Create booking**](../reference/rest-api.yaml/paths/~1bookings/post), [**Create draft booking**](../reference/rest-api.yaml/paths/~1bookings~1draft/post), and [**Update booking**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}/put) (with merge semantics). The field is returned in [**Get booking**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}/get) responses and can be opted into via the [**booking webhook**](booking-webhook.md) `include.metadata` flag (REST API).
- **Booking webhook event channel filter** — A new `eventChannels` filter can be added to [**booking webhook**](booking-webhook.md) subscriptions to filter events by the application that triggered them (e.g. only fire when a booking is updated from POS). Unlike the existing `channels` filter — which filters on where the booking was *created* — `eventChannels` filters on what application performed the specific action. Backwards compatible: existing subscriptions without this filter continue to receive events from all channels (REST API).

---

## 2026-05

### Added

- `multiPass` property to the [**redemption detail**](redemption-webhook.md) payload sent with redemption webhooks (REST API).

### Changed

- Added the ability to filter by `productType` and `productSubType` to [**Get products**](../reference/reporting-api.yaml/paths/~1data~1products/get) (Reporting API) and [**Get product detail**](../reference/rest-api.yaml/paths/~1products/get) (REST API).

---

## 2026-04

### Added

- Itemised `discounts` to [**Get bookings**](../reference/reporting-api.yaml/paths/~1data~1bookingitems/get) (Reporting API).

---

## 2026-03

### Added

- Ability to **get**, **create**, **update**, and **delete** venue staff accounts (REST API). [**Available upon request**](https://helpcenter.roller.software/).
- Ability to generate and cancel payment links for bookings via API (REST API):
  - [**Add payment link**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}~1payments~1links/post) (REST API).
  - [**Cancel payment link**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}~1payments~1links~1{paymentLinkId}/delete) (REST API).
  - [**Payment link webhook**](payment-link-webhook.md) to be notified when a payment is submitted against a new payment link.
- `taxComponents` property to [**Get venue detail**](../reference/rest-api.yaml/paths/~1venues~1me/get) (REST API).
- `ianaTimeZone` property to [**Get venue detail**](../reference/rest-api.yaml/paths/~1venues~1me/get) (REST API).

---

## 2026-02

### Added

- `automaticCancelHours` property to [**Create booking**](../reference/rest-api.yaml/paths/~1bookings/post) (REST API).

---

## 2026-01

### Added

- `operatorName` property to [**Get POS till reconciliations**](../reference/reporting-api.yaml/paths/~1data~1tillreconciliations/get) (Reporting API).
- A list of booking `payments` to [**Get booking detail**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}/get), and as an available inclusion for [**booking webhooks**](booking-webhook.md) (REST API).

---

## 2025-11

### Added

- `acceptMarketingSms` property to [**Get customers**](../reference/reporting-api.yaml/paths/~1data~1customers/get) (Reporting API), and to [**Create a booking**](../reference/rest-api.yaml/paths/~1bookings/post), [**Create draft booking**](../reference/rest-api.yaml/paths/~1bookings~1draft/post), [**Get guest detail**](../reference/rest-api.yaml/paths/~1guests~1{guestId}/get), and [**Update guest detail**](../reference/rest-api.yaml/paths/~1guests~1{guestId}/put) (REST API).

---

## 2025-10

### Added

- [**Signed waivers webhook**](signed-waiver-webhook.md) to be notified when a new waiver is signed.
- [**Get signed waivers**](../reference/rest-api.yaml/paths/~1signed-waivers~1{signedWaiverId}/get) endpoint (REST API).
- `multiVenueGiftCardReceivable` and `multiVenueGiftCardPayable` properties to [**Get revenue entries**](../reference/reporting-api.yaml/paths/~1reporting~1revenue-entries/get) (Reporting API).

### Changed

- Added _"Modifying assigned resources for booking items"_ as a new [**booking webhook**](booking-webhook.md) `Updated` trigger.

---

## 2025-09

### Added

- `taxIdentificationNumber` property to [**Get guest detail**](../reference/rest-api.yaml/paths/~1guests~1{guestId}/get), [**Update guest detail**](../reference/rest-api.yaml/paths/~1guests~1{guestId}/put), [**Create draft booking**](../reference/rest-api.yaml/paths/~1bookings~1draft/post), and [**Create booking**](../reference/rest-api.yaml/paths/~1bookings/post) (REST API), and to [**Get customers**](../reference/reporting-api.yaml/paths/~1data~1customers/get) (Reporting API).

---

## 2025-08

### Added

- Ability to manage stock products (REST API):
  - [**Create stock products**](../reference/rest-api.yaml/paths/~1products~1stock/post) (REST API).
  - [**Update stock products**](../reference/rest-api.yaml/paths/~1products~1stock/put) (REST API).
  - [**Update stock quantity**](../reference/rest-api.yaml/paths/~1products~1stock~1{parentProductId}~1quantity/put) (REST API).
- `fees`, `feeTax`, `subTotal`, and `subTotalTax` properties to [**Get booking costs**](../reference/rest-api.yaml/paths/~1bookings~1draft~1costs/post) (REST API).
- Booking modifiers `quantity` to [**Get bookings**](../reference/reporting-api.yaml/paths/~1data~1bookingitems/get) (Reporting API).

### Fixed

- Issue where booking modifiers would sometimes be missing or have an incorrect `amount` value (Reporting API).

---

## 2025-07

### Added

- `quantity` property to [**Get booking detail**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}/get) (REST API).
- `manualGiftCardAdjustment` property to [**Get revenue entries**](../reference/reporting-api.yaml/paths/~1reporting~1revenue-entries/get) to surface manual gift card adjustments (Reporting API).
- `taxes` property to [**Get venue detail**](../reference/rest-api.yaml/paths/~1venues~1me/get) to return a list of tax rates defined for the venue (REST API).
- `price`, `taxId`, `barcodeId`, `costOfGoods`, and `parLevel` properties to [**Get product detail**](../reference/rest-api.yaml/paths/~1products/get) (REST API).
- `price`, `taxId`, `barcodeId`, `costOfGoods`, and `parLevel` properties to [**Get products**](../reference/reporting-api.yaml/paths/~1data~1products/get) (Reporting API).

---

## 2025-06

### Fixed

- Issue where [**Get booking detail**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}/get) did not return discounts at the booking item level (REST API).
- Issue where [**Get reporting categories**](../reference/reporting-api.yaml/paths/~1data~1reportingcategories/get) did not return all product IDs when using HQ reporting category syncs (Reporting API).

---

## 2025-05

### Added

- Ability to update ticket `name` via the [**Update a booking**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}/put) endpoint (REST API).
- [**Update guest detail**](../reference/rest-api.yaml/paths/~1guests~1{guestId}/put) endpoint (REST API).
- Ability to backfill historical data over multiple days via the [**Bulk Export API**](bulk-exports-overview.md):
  - [**Bulk export request**](../reference/reporting-api.yaml/paths/~1reporting~1bulk/post) for requesting asynchronous data downloads via the bulk export webhook.
  - [**Bulk export webhook**](bulk-export-webhook.md) to be notified when bulk export requests are complete.
- `ticketCapacityRemaining` and `resourceCapacityRemaining` properties to the [**Get product availability**](../reference/rest-api.yaml/paths/~1product-availability/get) endpoint (REST API).
- Ability to [**manage discounts**](discounts.md) and discount codes (REST API):
  - [**Get discount**](../reference/rest-api.yaml/paths/~1discounts~1{discountId}/get) (REST API).
  - [**Create discount**](../reference/rest-api.yaml/paths/~1discounts/post) (REST API).
  - [**Update discount**](../reference/rest-api.yaml/paths/~1discounts~1{discountId}/put) (REST API).
  - [**Create discount codes**](../reference/rest-api.yaml/paths/~1discounts~1{discountId}~1codes/post) for adding to existing discounts (REST API).
  - [**Delete discount codes**](../reference/rest-api.yaml/paths/~1discounts~1{discountId}~1codes/delete) from existing discounts (REST API).
- [**Get guest detail**](../reference/rest-api.yaml/paths/~1guests~1{guestId}/get) endpoint to replace "get customer detail" (REST API).

### Changed

- Added "delete guest" as a trigger for `Updated` events on the [**guest webhook**](guest-webhook.md).

### Deprecated

- Marked [**Get customer detail**](../reference/rest-api.yaml/paths/~1customers~1{customerId}/get) as deprecated as part of renaming "customer" to "guest" (REST API).

---

## 2025-04

### Added

- Ability to use [**ROLLER Payments via API**](roller-payments-workflow.md) to process transactions when creating bookings (REST API).

### Changed

- Added the ability to filter by **product category** when registering triggers for the [**redemption webhook**](redemption-webhook.md).

---

## 2025-03

### Fixed

- Issue where the `cost` field returned by [**Get booking detail**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}/get) sometimes returned an empty value (REST API).

---

## 2025-02

### Added

- Ability to validate ticket redemptions by the time they were redeemed, using existing redemption devices configured in Venue Manager (REST API):
  - `redemptionDevice` property to [**Redeem tickets**](../reference/rest-api.yaml/paths/~1redemptions/post) (REST API).
- Ability to manage blocked capacity (REST API):
  - [**Search blocked capacity**](../reference/rest-api.yaml/paths/~1capacity-reservation~1block/get) (REST API).
  - [**Get blocked capacity**](../reference/rest-api.yaml/paths/~1capacity-reservation~1block~1{blockId}/get) (REST API).
  - [**Block capacity**](../reference/rest-api.yaml/paths/~1capacity-reservation~1block/post) (REST API).
  - [**Delete blocked capacity**](../reference/rest-api.yaml/paths/~1capacity-reservation~1block~1{blockId}/delete) (REST API).
- Guest `flags` to [**Get customers**](../reference/reporting-api.yaml/paths/~1data~1customers/get) (Reporting API).
- Guest `flags` to [**Get customer detail**](../reference/rest-api.yaml/paths/~1customers~1{customerId}/get) (REST API).
- `BookingUniqueId`, `meta`: { `ExternalBookingId` }, `bookingName`, `bookingPosNotes`, `bookingTotal`, `bookingFeeAmount`, and `bookingEndDate` properties to [**Get bookings**](../reference/reporting-api.yaml/paths/~1data~1bookingitems/get) (Reporting API).
- `bookingEndDate` and `customTicketId` properties to [**Update a booking**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}/put) (REST API).
- `posNotes` property to [**Get booking detail**](../reference/rest-api.yaml/paths/~1bookings~1{uniqueId}/get) (REST API).
- `deviceId` property to the [**redemption webhook**](redemption-webhook.md) payload (REST API).

---

## 2025-01

### Changed

- Established a dedicated API Integration Team to take ownership of ROLLER's public APIs and documentation.
