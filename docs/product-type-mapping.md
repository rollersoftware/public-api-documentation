---
stoplight-id: 6e4snhv85tuk2
---

# Product Type Mapping

The `ProductType` and `ProductSubType` properties (for example, those returned via [**Get products**](../reference/data-api.yaml)) correspond to a type of product in ROLLER. The table below maps the property values to expect for each corresponding ROLLER product type.

| ROLLER product | ProductType | ProductSubType |
|---|---|---|
| Standard pass | `6` : `Pass` | `0` : Empty |
| Session pass | `6` : `Pass` | `7` : `Session` |
| Recurring pass | `6` : `Pass` | `4` : `RecurringSessions` |
| Package | `10` : `Package` | `0` : Empty |
| Party package | `13` : `PartyPackage` | `0` : Empty |
| Gift card | `9` : `GiftCard` | `0` : Empty |
| Membership | `6` : `Pass` | `5` : `Membership` |
| Stock | `7` : `AddOn` | `8` : `Stock` |
| Addon (standard) | `7` : `AddOn` | `0` : Empty |
| Addon (donation) | `7` : `AddOn` | `1` : `Donation` |
| Addon (open product) | `7` : `AddOn` | `3` : `OpenProduct` |
| Addon (external gift card) | `7` : `AddOn` | `6` : `ExternalGiftCard` |
| Wallet | `11` : `Wallet` | `0` : Empty |
| Cashless card | `12` : `CashlessCard` | `0` : Empty |

> **Modifiers** are not considered products, so they do not have a `ProductType` or `ProductSubType`.
