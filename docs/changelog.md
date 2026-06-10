---
stoplight-id: iglgjf34psufs
---

# Changelog

All notable changes to ROLLER's public APIs are documented here. This changelog follows the [Keep a Changelog](https://keepachangelog.com/) convention, adapted for ROLLER's release cadence.

Releases are grouped by month and listed most-recent-first. Within each release, changes are grouped by type:

- **Added** — New endpoints, webhooks, properties, or capabilities.
- **Changed** — Changes to naming, behaviour, performance, or documentation.
- **Deprecated** — Features still available but scheduled for removal.
- **Fixed** — Corrections that align actual behaviour with expected behaviour.

Each entry notes the affected API (Reporting API or REST API) and links to the relevant reference.

## 2026-05

### Added

- `multiPass` property to the [**redemption detail**](redemption-webhook.md) payload sent with redemption webhooks (REST API).

### Changed

- Added the ability to filter by `productType` and `productSubType` to [**Get products**](../reference/reporting-api.yaml) (Reporting API) and [**Get product detail**](../reference/rest-api.yaml) (REST API).

## 2026-04

### Added

- Itemised `discounts` to [**Get bookings**](../reference/reporting-api.yaml) (Reporting API).

## 2026-03

### Added

- Ability to **get**, **create**, **update**, and **delete** venue staff accounts (REST API). [**Available upon request**](https://helpcenter.roller.software/).
- Ability to generate and cancel payment links for bookings via API (REST API):
  - [**Add payment link**](../reference/rest-api.yaml) (REST API).
  - [**Cancel payment link**](../reference/rest-api.yaml) (REST API).
  - [**Payment link webhook**](payment-link-webhook.md) to be notified when a payment is submitted against a new payment link.
- `taxComponents` property to [**Get venue detail**](../reference/rest-api.yaml) (REST API).
- `ianaTimeZone` property to [**Get venue detail**](../reference/rest-api.yaml) (REST API).

## 2026-02

### Added

- `automaticCancelHours` property to [**Create booking**](../reference/rest-api.yaml) (REST API).

## 2026-01

### Added

- `operatorName` property to [**Get POS till reconciliations**](../reference/reporting-api.yaml) (Reporting API).
- A list of booking `payments` to [**Get booking detail**](../reference/rest-api.yaml), and as an available inclusion for [**booking webhooks**](booking-webhook.md) (REST API).

## 2025-11

### Added

- `acceptMarketingSms` property to [**Get customers**](../reference/reporting-api.yaml) (Reporting API), and to [**Create a booking**](../reference/rest-api.yaml), [**Create draft booking**](../reference/rest-api.yaml), [**Get guest detail**](../reference/rest-api.yaml), and [**Update guest detail**](../reference/rest-api.yaml) (REST API).

## 2025-10

### Added

- [**Signed waivers webhook**](signed-waiver-webhook.md) to be notified when a new waiver is signed.
- [**Get signed waivers**](../reference/rest-api.yaml) endpoint (REST API).
- `multiVenueGiftCardReceivable` and `multiVenueGiftCardPayable` properties to [**Get revenue entries**](../reference/reporting-api.yaml) (Reporting API).

### Changed

- Added _"Modifying assigned resources for booking items"_ as a new [**booking webhook**](booking-webhook.md) `Updated` trigger.

## 2025-09

### Added

- `taxIdentificationNumber` property to [**Get guest detail**](../reference/rest-api.yaml), [**Update guest detail**](../reference/rest-api.yaml), [**Create draft booking**](../reference/rest-api.yaml), and [**Create booking**](../reference/rest-api.yaml) (REST API), and to [**Get customers**](../reference/reporting-api.yaml) (Reporting API).

## 2025-08

### Added

- Ability to manage stock products (REST API):
  - [**Create stock products**](../reference/rest-api.yaml) (REST API).
  - [**Update stock products**](../reference/rest-api.yaml) (REST API).
  - [**Update stock quantity**](../reference/rest-api.yaml) (REST API).
- `fees`, `feeTax`, `subTotal`, and `subTotalTax` properties to [**Get booking costs**](../reference/rest-api.yaml) (REST API).
- Booking modifiers `quantity` to [**Get bookings**](../reference/reporting-api.yaml) (Reporting API).

### Fixed

- Issue where booking modifiers would sometimes be missing or have an incorrect `amount` value (Reporting API).

## 2025-07

### Added

- `quantity` property to [**Get booking detail**](../reference/rest-api.yaml) (REST API).
- `manualGiftCardAdjustment` property to [**Get revenue entries**](../reference/reporting-api.yaml) to surface manual gift card adjustments (Reporting API).
- `taxes` property to [**Get venue detail**](../reference/rest-api.yaml) to return a list of tax rates defined for the venue (REST API).
- `price`, `taxId`, `barcodeId`, `costOfGoods`, and `parLevel` properties to [**Get product detail**](../reference/rest-api.yaml) (REST API).
- `price`, `taxId`, `barcodeId`, `costOfGoods`, and `parLevel` properties to [**Get products**](../reference/reporting-api.yaml) (Reporting API).

## 2025-06

### Fixed

- Issue where [**Get booking detail**](../reference/rest-api.yaml) did not return discounts at the booking item level (REST API).
- Issue where [**Get reporting categories**](../reference/reporting-api.yaml) did not return all product IDs when using HQ reporting category syncs (Reporting API).

## 2025-05

### Added

- Ability to update ticket `name` via the [**Update a booking**](../reference/rest-api.yaml) endpoint (REST API).
- [**Update guest detail**](../reference/rest-api.yaml) endpoint (REST API).
- Ability to backfill historical data over multiple days via the [**Bulk Export API**](https://docs.roller.app/docs/bulk-exports/66otoe75x30hk):
  - [**Bulk export request**](https://docs.roller.app/docs/bulk-exports/w8rlc9iamhm5j) for requesting asynchronous data downloads via the bulk export webhook.
  - [**Bulk export webhook**](bulk-export-webhook.md) to be notified when bulk export requests are complete.
- `ticketCapacityRemaining` and `resourceCapacityRemaining` properties to the [**Get product availability**](../reference/rest-api.yaml) endpoint (REST API).
- Ability to [**manage discounts**](discounts.md) and discount codes (REST API):
  - [**Get discount**](../reference/rest-api.yaml) (REST API).
  - [**Create discount**](../reference/rest-api.yaml) (REST API).
  - [**Update discount**](../reference/rest-api.yaml) (REST API).
  - [**Create discount codes**](../reference/rest-api.yaml) for adding to existing discounts (REST API).
  - [**Delete discount codes**](../reference/rest-api.yaml) from existing discounts (REST API).
- [**Get guest detail**](../reference/rest-api.yaml) endpoint to replace "get customer detail" (REST API).

### Changed

- Added "delete guest" as a trigger for `Updated` events on the [**guest webhook**](guest-webhook.md).

### Deprecated

- Marked [**Get customer detail**](../reference/rest-api.yaml) as deprecated as part of renaming "customer" to "guest" (REST API).

## 2025-04

### Added

- Ability to use [**ROLLER Payments via API**](https://docs.roller.app/docs/roller-payments/e4x9qrxpg5iwd) to process transactions when creating bookings (REST API).

### Changed

- Added the ability to filter by **product category** when registering triggers for the [**redemption webhook**](redemption-webhook.md).

## 2025-03

### Fixed

- Issue where the `cost` field returned by [**Get booking detail**](../reference/rest-api.yaml) sometimes returned an empty value (REST API).

## 2025-02

### Added

- Ability to validate ticket redemptions by the time they were redeemed, using existing redemption devices configured in Venue Manager (REST API):
  - `redemptionDevice` property to [**Redeem tickets**](../reference/rest-api.yaml) (REST API).
- Ability to manage blocked capacity (REST API):
  - [**Search blocked capacity**](../reference/rest-api.yaml) (REST API).
  - [**Get blocked capacity**](../reference/rest-api.yaml) (REST API).
  - [**Block capacity**](../reference/rest-api.yaml) (REST API).
  - [**Delete blocked capacity**](../reference/rest-api.yaml) (REST API).
- Guest `flags` to [**Get customers**](../reference/reporting-api.yaml) (Reporting API).
- Guest `flags` to [**Get customer detail**](../reference/rest-api.yaml) (REST API).
- `BookingUniqueId`, `meta`: { `ExternalBookingId` }, `bookingName`, `bookingPosNotes`, `bookingTotal`, `bookingFeeAmount`, and `bookingEndDate` properties to [**Get bookings**](../reference/reporting-api.yaml) (Reporting API).
- `bookingEndDate` and `customTicketId` properties to [**Update a booking**](../reference/rest-api.yaml) (REST API).
- `posNotes` property to [**Get booking detail**](../reference/rest-api.yaml) (REST API).
- `deviceId` property to the [**redemption webhook**](redemption-webhook.md) payload (REST API).

## 2025-01

### Changed

- Established a dedicated API Integration Team to take ownership of ROLLER's public APIs and documentation.
