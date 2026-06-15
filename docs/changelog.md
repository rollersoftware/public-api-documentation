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

- New [**Get NetSuite settings**](https://docs.roller.app/docs/api/rest/operations/get-netsuite-settings) and [**Update NetSuite settings**](https://docs.roller.app/docs/api/rest/operations/update-netsuite-settings) endpoints to manage NetSuite integration settings for a venue: `locationId` (maps the ROLLER venue to a NetSuite location for consolidated reporting) and `exportId` (prefix for NetSuite export row IDs) (REST API).
- [**Get product availability calendar**](https://docs.roller.app/docs/api/rest/operations/get-product-availability-calendar) endpoint (`GET /product-availability/calendar`) to retrieve the availability status for each day in a given month for a single product. Designed for date picker and calendar UIs in third-party checkouts (REST API).
- **Booking metadata** — User-defined key-value pairs can now be stored against bookings. The `metadata` property is supported on [**Create booking**](https://docs.roller.app/docs/api/rest/operations/create-a-booking), [**Create draft booking**](https://docs.roller.app/docs/api/rest/operations/create-draft-booking), and [**Update booking**](https://docs.roller.app/docs/api/rest/operations/update-a-booking) (with merge semantics). The field is returned in [**Get booking**](https://docs.roller.app/docs/api/rest/operations/get-booking-detail) responses and can be opted into via the [**booking webhook**](booking-webhook.md) `include.metadata` flag (REST API).
- **Booking webhook event channel filter** — A new `eventChannels` filter can be added to [**booking webhook**](booking-webhook.md) subscriptions to filter events by the application that triggered them (e.g. only fire when a booking is updated from POS). Unlike the existing `channels` filter — which filters on where the booking was *created* — `eventChannels` filters on what application performed the specific action. Backwards compatible: existing subscriptions without this filter continue to receive events from all channels (REST API).

---

## 2026-05

### Added

- `multiPass` property to the [**redemption detail**](redemption-webhook.md) payload sent with redemption webhooks (REST API).

### Changed

- Added the ability to filter by `productType` and `productSubType` to [**Get products**](https://docs.roller.app/docs/api/reporting/operations/get-products) (Reporting API) and [**Get product detail**](https://docs.roller.app/docs/api/rest/operations/get-product-detail) (REST API).

---

## 2026-04

### Added

- Itemised `discounts` to [**Get bookings**](https://docs.roller.app/docs/api/reporting/operations/get-bookings) (Reporting API).

---

## 2026-03

### Added

- Ability to **get**, **create**, **update**, and **delete** venue staff accounts (REST API). [**Available upon request**](https://helpcenter.roller.software/).
- Ability to generate and cancel payment links for bookings via API (REST API):
  - [**Add payment link**](https://docs.roller.app/docs/api/rest/operations/create-payment-link) (REST API).
  - [**Cancel payment link**](https://docs.roller.app/docs/api/rest/operations/cancel-payment-link) (REST API).
  - [**Payment link webhook**](payment-link-webhook.md) to be notified when a payment is submitted against a new payment link.
- `taxComponents` property to [**Get venue detail**](https://docs.roller.app/docs/api/rest/operations/get-venue-detail) (REST API).
- `ianaTimeZone` property to [**Get venue detail**](https://docs.roller.app/docs/api/rest/operations/get-venue-detail) (REST API).

---

## 2026-02

### Added

- `automaticCancelHours` property to [**Create booking**](https://docs.roller.app/docs/api/rest/operations/create-a-booking) (REST API).

---

## 2026-01

### Added

- `operatorName` property to [**Get POS till reconciliations**](https://docs.roller.app/docs/api/reporting/operations/get-pos-till-reconciliations) (Reporting API).
- A list of booking `payments` to [**Get booking detail**](https://docs.roller.app/docs/api/rest/operations/get-booking-detail), and as an available inclusion for [**booking webhooks**](booking-webhook.md) (REST API).

---

## 2025-11

### Added

- `acceptMarketingSms` property to [**Get customers**](https://docs.roller.app/docs/api/reporting/operations/get-customers) (Reporting API), and to [**Create a booking**](https://docs.roller.app/docs/api/rest/operations/create-a-booking), [**Create draft booking**](https://docs.roller.app/docs/api/rest/operations/create-draft-booking), [**Get guest detail**](https://docs.roller.app/docs/api/rest/operations/get-guest-detail), and [**Update guest detail**](https://docs.roller.app/docs/api/rest/operations/update-guest-detail) (REST API).

---

## 2025-10

### Added

- [**Signed waivers webhook**](signed-waiver-webhook.md) to be notified when a new waiver is signed.
- [**Get signed waivers**](https://docs.roller.app/docs/api/rest/operations/get-signed-waiver) endpoint (REST API).
- `multiVenueGiftCardReceivable` and `multiVenueGiftCardPayable` properties to [**Get revenue entries**](https://docs.roller.app/docs/api/reporting/operations/get-revenue-entries) (Reporting API).

### Changed

- Added _"Modifying assigned resources for booking items"_ as a new [**booking webhook**](booking-webhook.md) `Updated` trigger.

---

## 2025-09

### Added

- `taxIdentificationNumber` property to [**Get guest detail**](https://docs.roller.app/docs/api/rest/operations/get-guest-detail), [**Update guest detail**](https://docs.roller.app/docs/api/rest/operations/update-guest-detail), [**Create draft booking**](https://docs.roller.app/docs/api/rest/operations/create-draft-booking), and [**Create booking**](https://docs.roller.app/docs/api/rest/operations/create-a-booking) (REST API), and to [**Get customers**](https://docs.roller.app/docs/api/reporting/operations/get-customers) (Reporting API).

---

## 2025-08

### Added

- Ability to manage stock products (REST API):
  - [**Create stock products**](https://docs.roller.app/docs/api/rest/operations/create-stock-products) (REST API).
  - [**Update stock products**](https://docs.roller.app/docs/api/rest/operations/update-stock-products) (REST API).
  - [**Update stock quantity**](https://docs.roller.app/docs/api/rest/operations/update-stock-quantity) (REST API).
- `fees`, `feeTax`, `subTotal`, and `subTotalTax` properties to [**Get booking costs**](https://docs.roller.app/docs/api/rest/operations/get-booking-costs) (REST API).
- Booking modifiers `quantity` to [**Get bookings**](https://docs.roller.app/docs/api/reporting/operations/get-bookings) (Reporting API).

### Fixed

- Issue where booking modifiers would sometimes be missing or have an incorrect `amount` value (Reporting API).

---

## 2025-07

### Added

- `quantity` property to [**Get booking detail**](https://docs.roller.app/docs/api/rest/operations/get-booking-detail) (REST API).
- `manualGiftCardAdjustment` property to [**Get revenue entries**](https://docs.roller.app/docs/api/reporting/operations/get-revenue-entries) to surface manual gift card adjustments (Reporting API).
- `taxes` property to [**Get venue detail**](https://docs.roller.app/docs/api/rest/operations/get-venue-detail) to return a list of tax rates defined for the venue (REST API).
- `price`, `taxId`, `barcodeId`, `costOfGoods`, and `parLevel` properties to [**Get product detail**](https://docs.roller.app/docs/api/rest/operations/get-product-detail) (REST API).
- `price`, `taxId`, `barcodeId`, `costOfGoods`, and `parLevel` properties to [**Get products**](https://docs.roller.app/docs/api/reporting/operations/get-products) (Reporting API).

---

## 2025-06

### Fixed

- Issue where [**Get booking detail**](https://docs.roller.app/docs/api/rest/operations/get-booking-detail) did not return discounts at the booking item level (REST API).
- Issue where [**Get reporting categories**](https://docs.roller.app/docs/api/reporting/operations/get-reporting-categories) did not return all product IDs when using HQ reporting category syncs (Reporting API).

---

## 2025-05

### Added

- Ability to update ticket `name` via the [**Update a booking**](https://docs.roller.app/docs/api/rest/operations/update-a-booking) endpoint (REST API).
- [**Update guest detail**](https://docs.roller.app/docs/api/rest/operations/update-guest-detail) endpoint (REST API).
- Ability to backfill historical data over multiple days via the [**Bulk Export API**](bulk-exports-overview.md):
  - [**Bulk export request**](https://docs.roller.app/docs/api/reporting/operations/bulk-data-export-request) for requesting asynchronous data downloads via the bulk export webhook.
  - [**Bulk export webhook**](bulk-export-webhook.md) to be notified when bulk export requests are complete.
- `ticketCapacityRemaining` and `resourceCapacityRemaining` properties to the [**Get product availability**](https://docs.roller.app/docs/api/rest/operations/get-product-availability) endpoint (REST API).
- Ability to [**manage discounts**](discounts.md) and discount codes (REST API):
  - [**Get discount**](https://docs.roller.app/docs/api/rest/operations/get-discount) (REST API).
  - [**Create discount**](https://docs.roller.app/docs/api/rest/operations/create-discount) (REST API).
  - [**Update discount**](https://docs.roller.app/docs/api/rest/operations/update-discount) (REST API).
  - [**Create discount codes**](https://docs.roller.app/docs/api/rest/operations/create-discount-codes) for adding to existing discounts (REST API).
  - [**Delete discount codes**](https://docs.roller.app/docs/api/rest/operations/delete-discount-codes) from existing discounts (REST API).
- [**Get guest detail**](https://docs.roller.app/docs/api/rest/operations/get-guest-detail) endpoint to replace "get customer detail" (REST API).

### Changed

- Added "delete guest" as a trigger for `Updated` events on the [**guest webhook**](guest-webhook.md).

### Deprecated

- Marked [**Get customer detail**](https://docs.roller.app/docs/api/rest/operations/get-customer-detail) as deprecated as part of renaming "customer" to "guest" (REST API).

---

## 2025-04

### Added

- Ability to use [**ROLLER Payments via API**](roller-payments-workflow.md) to process transactions when creating bookings (REST API).

### Changed

- Added the ability to filter by **product category** when registering triggers for the [**redemption webhook**](redemption-webhook.md).

---

## 2025-03

### Fixed

- Issue where the `cost` field returned by [**Get booking detail**](https://docs.roller.app/docs/api/rest/operations/get-booking-detail) sometimes returned an empty value (REST API).

---

## 2025-02

### Added

- Ability to validate ticket redemptions by the time they were redeemed, using existing redemption devices configured in Venue Manager (REST API):
  - `redemptionDevice` property to [**Redeem tickets**](https://docs.roller.app/docs/api/rest/operations/redeem-tickets) (REST API).
- Ability to manage blocked capacity (REST API):
  - [**Search blocked capacity**](https://docs.roller.app/docs/api/rest/operations/search-resource-capacity-blocks) (REST API).
  - [**Get blocked capacity**](https://docs.roller.app/docs/api/rest/operations/get-resource-capacity-block) (REST API).
  - [**Block capacity**](https://docs.roller.app/docs/api/rest/operations/block-resource-capacity) (REST API).
  - [**Delete blocked capacity**](https://docs.roller.app/docs/api/rest/operations/delete-resource-capacity-block) (REST API).
- Guest `flags` to [**Get customers**](https://docs.roller.app/docs/api/reporting/operations/get-customers) (Reporting API).
- Guest `flags` to [**Get customer detail**](https://docs.roller.app/docs/api/rest/operations/get-customer-detail) (REST API).
- `BookingUniqueId`, `meta`: { `ExternalBookingId` }, `bookingName`, `bookingPosNotes`, `bookingTotal`, `bookingFeeAmount`, and `bookingEndDate` properties to [**Get bookings**](https://docs.roller.app/docs/api/reporting/operations/get-bookings) (Reporting API).
- `bookingEndDate` and `customTicketId` properties to [**Update a booking**](https://docs.roller.app/docs/api/rest/operations/update-a-booking) (REST API).
- `posNotes` property to [**Get booking detail**](https://docs.roller.app/docs/api/rest/operations/get-booking-detail) (REST API).
- `deviceId` property to the [**redemption webhook**](redemption-webhook.md) payload (REST API).

---

## 2025-01

### Changed

- Established a dedicated API Integration Team to take ownership of ROLLER's public APIs and documentation.
