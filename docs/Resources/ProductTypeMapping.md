---
stoplight-id: 6e4snhv85tuk2
---

# Product Type Mapping

The properties `ProductType` and `ProductSubType` (for example returned via [**get products**](https://roller.stoplight.io/docs/roller-api/reference/Data%20API/DataAPI.yaml/paths/~1data~1products/get)) correspond to a type of product in ROLLER. Below is a table mapping what property values to expect for each corresponding ROLLER product type.

ROLLER Product | ProductType | ProductSubType
-|-|-
Standard pass | `6` : `Pass` | `0` : Empty
Session pass | `6` : `Pass` | `7` : `Session`
Recurring pass | `6` : `Pass` | `4` : `RecurringSessions`
Package | `10` : `Package` | `0` : Empty
Party package | `13` : `PartyPackage` | `0` : Empty
Gift card | `9` : `GiftCard` | `0` : Empty
Membership | `6` : `Pass` | `5` : `Membership`
Stock | `7` : `AddOn` | `8` : `Stock`
Addon (Standard) | `7` : `AddOn` | `0` : Empty
Addon (Donation) | `7` : `AddOn` | `1` : `Donation`
Addon (Open Product) | `7` : `AddOn` | `3` : `OpenProduct`
Addon (External gift card) | `7` : `AddOn` | `6` : `ExternalGiftCard`
Wallet | `11` : `Wallet` | `0` : Empty
Cashless card | `12` : `CashlessCard` | `0` : Empty

> Please note **Modifiers** are not considered products, so do not have a `ProductType` or `ProductSubType`