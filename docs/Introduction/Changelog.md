---
stoplight-id: iglgjf34psufs
---

# Changelog

> 📝 **Legend**
>
> - 🖼️ New Function — Several added changes to achieve an overall objective
> - 🧩 New Interface — Newly added endpoint or webhook
> - 🏷️ New Property — Newly added property to an existing data structure
> - 🔧 Improvement — Any changes to naming, behaviour, performance or documentation
> - 🐛 Bug Fix — Corrections to align actual behaviour with expected behaviour

**The following table captures recent key changes to ROLLER's Public APIs:**

| RELEASE | CHANGE                | DESCRIPTION                                                                                                                                                                                                                                 |
| ------- | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |   
| MAY26 | 🏷️ New Property      | ???Added itemised `discounts` to [**get bookings**](https://docs.roller.app/docs/roller-api/15e02538d6f25) on the DataAPI???
| MAY26 | 🔧 Improvement        | Added ability to filter by `productType` and `productSubType` to [**get products**](https://docs.roller.app/docs/roller-api/7bbac8eaac480) and [**get product detail**](https://docs.roller.app/docs/rest-api/4036b3635053a)
| MAY26 | 🏷️ New Property      | Added `multiPass` to [**redemption detail**](https://docs.roller.app/docs/rest-api/jeh5xeo9m5pt6) payload that is sent with redemption webhooks
| APR26 | 🏷️ New Property      | Added itemised `discounts` to [**get bookings**](https://docs.roller.app/docs/roller-api/15e02538d6f25) on the DataAPI
| MAR26   | 🖼️ New Function      | Added ability to **Get**, **Create**, **Update**, and **Delete** venue staff accounts via RestAPI. [**Available upon request**](https://helpcenter.roller.software/).
| MAR26 | 🏷️ New Property      | Added `taxComponents` to [**get venue detail**](https://docs.roller.app/docs/rest-api/e2c768c93c2d6) on the RestAPI
| MAR26 | 🏷️ New Property      | Added `ianaTimeZone` to [**get venue detail**](https://docs.roller.app/docs/rest-api/e2c768c93c2d6) on the RestAPI
| MAR26   | 🖼️ New Function      | Added ability to generate and cancel payment links for bookings via API
| -   | 🧩 New Interface      | Added [**add payment link**](https://docs.roller.app/docs/rest-api/hzi18m1t6nee5) to the RestAPI
| -   | 🧩 New Interface      | Added [**cancel payment link**](https://docs.roller.app/docs/rest-api/4svhhqdspro2l) to the RestAPI
| - | 🧩 New Interface      | Added a [**payment link webhook**](https://docs.roller.app/docs/webhooks/7gn4zuznopwes) to be notified when a new payment link has payment submitted
| FEB26 | 🏷️ New Property      | Added `automaticCancelHours` to [**create booking**](https://docs.roller.app/docs/rest-api/5703708522c6b) on the RestAPI
| JAN26 | 🏷️ New Property      | Added `operatorName` to [**get POS till reconciliations**](https://docs.roller.app/docs/roller-api/b705c76e55e76) on the DataAPI
| JAN26 | 🏷️ New Property      | Added a list of booking `payments` to [**get booking detail**](https://docs.roller.app/docs/rest-api/olt8a8nxs75ev) and as an available inclusion for [**booking webhooks**](https://docs.roller.app/docs/rest-api/3a934c551891e)
| NOV25 | 🏷️ New Property      | Added `acceptMarketingSms` to [**get customers**](https://docs.roller.app/docs/roller-api/67bddadddf571) via DataAPI and [**create a booking**](https://docs.roller.app/docs/rest-api/5703708522c6b), [**create draft booking**](https://docs.roller.app/docs/rest-api/516f25029993a), [**get guest detail**](https://docs.roller.app/docs/rest-api/ee8wtxgbkc0ut), [**update guest detail**](https://docs.roller.app/docs/rest-api/2cfjtwtpmlzp4) via RestAPI
| OCT25 | 🧩 New Interface      | Added [**signed waivers webhook**](https://docs.roller.app/docs/webhooks/vynaklh7qg8d1) to be notified when a new waiver is signed  
| OCT25 | 🧩 New Interface      | Added [**get signed waivers**](https://docs.roller.app/docs/rest-api/ajx7r36nll3ez) to the RestAPI
| OCT25   | 🔧 Improvement      | Added _"Modifying assigned resources for booking items"_ as a new [**Booking Webhook**](https://docs.roller.app/docs/webhooks/branches/main/1tjb4whgq33f0) `Updated` trigger
| OCT25   | 🏷️ New Property      | Added `multiVenueGiftCardReceivable` and `multiVenueGiftCardPayable` to [**get revenue entries**](https://docs.roller.app/docs/roller-api/branches/main/5cc8264046482) via the DataAPI
| SEP25   | 🏷️ New Property      | Added `taxIdentificationNumber` to [**get guest detail**](https://docs.roller.app/docs/rest-api/ee8wtxgbkc0ut), [**update guest detail**](https://docs.roller.app/docs/rest-api/2cfjtwtpmlzp4), [**create draft booking**](https://docs.roller.app/docs/rest-api/516f25029993a) and [**create booking**](https://docs.roller.app/docs/rest-api/5703708522c6b) via the RestAPI, and [**get customers**](https://docs.roller.app/docs/roller-api/branches/main/67bddadddf571) via the DataAPI
| AUG25   | 🏷️ New Property      | Added `fees`, `feeTax`, `subTotal`, `subTotalTax` to [**get booking costs**](https://docs.roller.app/docs/rest-api/branches/main/62e21c34b7ef3) via the RestAPI
| AUG25   | 🏷️ New Property      | Added booking modifiers `quantity` to [**get bookings**](https://docs.roller.app/docs/roller-api/15e02538d6f25) via the DataAPI
| AUG25   | 🐛 Bug Fix      | Fixed issue where sometimes booking modifiers would be missing or would have an incorrect `amount` value via the DataAPI 
| AUG25   | 🖼️ New Function      | Added ability to manage stock products via the RestAPI
| -   | 🧩 New Interface      | Added [**create stock products**](https://docs.roller.app/docs/rest-api/branches/main/ubj2tlego6it3) to the RestAPI
| -   | 🧩 New Interface      | Added [**update stock products**](https://docs.roller.app/docs/rest-api/branches/main/4tm9nigd46q92) to the RestAPI
| -   | 🧩 New Interface      | Added [**update stock quantity**](https://docs.roller.app/docs/rest-api/branches/main/7r5npm6bhkbps) to the RestAPI
| JUL25   | 🏷️ New Property      | Added `quantity` to [**get booking detail**](https://docs.roller.app/docs/rest-api/olt8a8nxs75ev) via the RestAPI
| JUL25   | 🏷️ New Property      | Added `manualGiftCardAdjustment` to [**get revenue entries**](https://docs.roller.app/docs/roller-api/5cc8264046482) to surface any manual gift card  adjustments                                                                           |
| JUL25   | 🏷️ New Property      | Added `taxes` to [**get venue detail**](https://docs.roller.app/docs/rest-api/branches/main/e2c768c93c2d6) to return a list of tax rates defined for the venue                                                                              |
| JUL25   | 🏷️ New Property      | Added `price`, `taxId`, `barcodeId`, `costOfGoods`, `parLevel` to [**get product detail**](https://docs.roller.app/docs/rest-api/4036b3635053a) via RestAPI                                                                             |
| JUL25   | 🏷️ New Property      | Added `price`, `taxId`, `barcodeId`, `costOfGoods`, `parLevel` to [**get products**](https://docs.roller.app/docs/roller-api/7bbac8eaac480) via DataAPI                                                                                 |
| JUN25   | 🐛 Bug Fix            | Fixed issue where [**get booking detail**](https://docs.roller.app/docs/rest-api/olt8a8nxs75ev) via RestAPI did not return discounts at booking item level                                                                                  |
| JUN25   | 🐛 Bug Fix            | Fixed issue where [**get reporting categories**](https://docs.roller.app/docs/roller-api/45e84b45de286) via DataAPI did not return all productID's if utilising HQ reporting category syncs                                                 |
| MAY25   | 🏷️ New Property      | Added ability to update ticket `name` to [**update a booking**](https://docs.roller.app/docs/rest-api/v4mzj4t4erwa9) endpoint via RestAPI                                                                                                   |
| MAY25   | 🔧 Improvement        | Added 'delete guest' as a trigger to `Updated` events for the [**guest webhook**](https://docs.roller.app/docs/webhooks/c9f31wv1iiubf)                                                                                                      |
| MAY25   | 🧩 New Interface      | Added [**update guest detail**](https://docs.roller.app/docs/rest-api/2cfjtwtpmlzp4) to RestAPI                                                                                                                                         |
| MAY25   | 🖼️ New Function | Added the ability to backfill historical data over multiple days via [**Bulk Export API**](https://docs.roller.app/docs/bulk-exports/66otoe75x30hk)                                                                                         |
| -       | 🧩 New Interface      | Added [**bulk export request**](https://docs.roller.app/docs/bulk-exports/w8rlc9iamhm5j) for requesting async downloading of data via bulk export webhook                                                                                   |
| -       | 🧩 New Interface      | Added new [**bulk export webhook**](https://docs.roller.app/docs/webhooks/qg14o9szv8d26) to be notified when bulk export requests are complete                                                                                              |
| MAY25   | 🏷️ New Property      | Added `ticketCapacityRemaining` and `resourceCapacityRemaining` properties to [**get product availability**](https://docs.roller.app/docs/rest-api/efb9788ea3808) endpoint via RestAPI.                                                     |
| MAY25   | 🖼️ New Function | Added the ability to [**manage discounts**](https://docs.roller.app/docs/rest-api/xy4jtgqlldj5o) and discount codes via RestAPI                                                                                                         |
| -       | 🧩 New Interface      | Added [**get discount**](https://docs.roller.app/docs/rest-api/bmsh1zsubdb7e) to RestAPI                                                                                                                                                    |
| -       | 🧩 New Interface      | Added ability to [**create discount**](https://docs.roller.app/docs/rest-api/ou0fhbpecax13) via RestAPI                                                                                                                                     |
| -       | 🧩 New Interface      | Added ability to [**update discount**](https://docs.roller.app/docs/rest-api/cvm27qdwoqjk2) via RestAPI                                                                                                                                     |
| -       | 🧩 New Interface      | Added ability to [**create discount codes**](https://docs.roller.app/docs/rest-api/armugwijxjpqd) for adding to existing discounts via RestAPI                                                                                              |
| -       | 🧩 New Interface      | Added ability to [**delete discount codes**](https://docs.roller.app/docs/rest-api/kd4qopxryu3cs) from existing discounts via RestAPI                                                                                                       |
| MAY25   | 🧩 New Interface      | Added [**get guest detail**](https://docs.roller.app/docs/rest-api/ee8wtxgbkc0ut) to replace "get customer detail" in RestAPI                                                                                                           |
| MAY25   | 🔧 Improvement        | Marked [**get customer detail**](https://docs.roller.app/docs/rest-api/rx9yreablf0rn) as **deprecated** to rename "customer" to "guest" via RestAPI                                                                                      |
| APR25   | 🖼️ New Function | Released ability to utilise [**ROLLER Payments via API**](https://docs.roller.app/docs/roller-payments/e4x9qrxpg5iwd) to process transactions when creating bookings via RestAPI.                                                       |
| APR25   | 🔧 Improvement        | Added the ability to filter by **Product Category** when registering triggers for the [**redemption webhook**](https://docs.roller.app/docs/webhooks/c9ntvneweithh)                                                                         |
| MAR25   | 🐛 Bug Fix            | Correction of issue where the `cost` field returned by [**get booking detail**](https://docs.roller.app/docs/rest-api/olt8a8nxs75ev) sometimes returned an empty value via RestAPI                                                      |
| FEB25   | 🖼️ New Function | Added the ability to validate ticket redemptions by the time they were redeemed, using existing redemption devices configured in VM, via RestAPI                                                                                        |
| -       | 🏷️ New Property      | Added `redemptionDevice` to [**redeem tickets**](https://docs.roller.app/docs/rest-api/fb1d84952285f) via RestAPI                                                                                                                        |
| FEB25   | 🖼️ New Function | Added ability to manage blocked capacity via RestAPI                                                                                                                                                                                        |
| -       | 🧩 New Interface      | Added [**search blocked capacity**](https://docs.roller.app/docs/rest-api/l05sayuiqmtk6) via RestAPI                                                                                                                                        |
| -       | 🧩 New Interface      | Added [**get blocked capacity**](https://docs.roller.app/docs/rest-api/a8e52r56hn5y1) via RestAPI                                                                                                                                           |
| -       | 🧩 New Interface      | Added ability to [**block capacity**](https://docs.roller.app/docs/rest-api/b50kcv6g4rn95) via RestAPI                                                                                                                                      |
| -       | 🧩 New Interface      | Added ability to [**delete blocked capacity**](https://docs.roller.app/docs/rest-api/nbs0n5tm0dirn) via RestAPI                                                                                                                             |
| FEB25   | 🏷️ New Property      | Added guest `flags` to [**get customers**](https://docs.roller.app/docs/roller-api/67bddadddf571) via DataAPI                                                                                                                               |
| FEB25   | 🏷️ New Property      | Added guest `flags` to [**get customer detail**](https://docs.roller.app/docs/roller-api/67bddadddf571) via RestAPI                                                                                                                         |
| FEB25   | 🏷️ New Property      | Added `BookingUniqueId`, `meta`: {`ExternalBookingId`}, `bookingName`, `bookingPosNotes`, `bookingTotal`, `bookingFeeAmount`, `bookingEndDate` to [**get bookings**](https://docs.roller.app/docs/roller-api/15e02538d6f25) via DataAPI |
| FEB25   | 🏷️ New Property      | Added `bookingEndDate`, `customTicketId` to [**update a booking**](https://docs.roller.app/docs/rest-api/v4mzj4t4erwa9) via RestAPI                                                                                                     |
| FEB25   | 🏷️ New Property      | Added `posNotes` to [**get booking detail**](https://docs.roller.app/docs/webhooks/c9ntvneweithh) via RestAPI                                                                                                                           |
| FEB25   | 🏷️ New Property      | Added `deviceId` to the [**redemption webhook**](https://docs.roller.app/docs/webhooks/c9ntvneweithh) payload returned via RestAPI                                                                                                      |
| JAN25   | 🔧 Improvement        | Officially created dedicated API Integration Team to take ownership of our Public API's and documentation                                                                                                                                   |
