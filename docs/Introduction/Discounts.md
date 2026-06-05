---
stoplight-id: xy4jtgqlldj5o
---

# Discounts

The RestAPI allows you to create and update discount configurations, including adding (or removing) usable `codes` to the discount. This enables external discount management, which can be used in scenarios such as:

- Registering promotional codes created by a 3rd party, such as those issued via email/sms marketing or on pre-printed voucher/coupon stock
- Automation of the regular, manual bulk-upload of discount codes

<!-- theme: warning -->
> #### Unsupported Scenarios
> Creating duplicate discount codes across several ROLLER platforms to enable multi-venue discounts is strongly discouraged due to the technical limitations it introduces. If you are interested in achieving this functionality please get in touch to register your interest.

---

## Available discount endpoints
* DataAPI > [**Get discounts**](https://docs.roller.app/docs/roller-api/56d02d8498025)
* RestAPI > [**Get discount**](https://docs.roller.app/docs/rest-api/bmsh1zsubdb7e)
* RestAPI > [**Update discount**](https://docs.roller.app/docs/rest-api/cvm27qdwoqjk2)
* RestAPI > [**Create discount**](https://docs.roller.app/docs/rest-api/ou0fhbpecax13)
* RestAPI > [**Create discount codes**](https://docs.roller.app/docs/rest-api/armugwijxjpqd)
* RestAPI > [**Delete discount codes**](https://docs.roller.app/docs/rest-api/kd4qopxryu3cs)
* RestAPI > [**Booking costs**](https://docs.roller.app/docs/rest-api/62e21c34b7ef3) (For **discount code validation**)

---

## What discount configurations are currently supported?

Discount `codes` can be added or removed for any discount in your venue, however creating and updating discounts via the Rest API can only be done with certain discount configurations:

Configuration | Supported?
-|-
Percentage discounts | ✅
Fixed amount discounts | ✅
Buy & Get discounts | ❌
Restricting booking dates | ✅
Limitations per application (sales channel) | ✅
`X` uses `Per code` limitations| ✅
"Issue codes on purchase" discounts | ❌
Configuring discounts apply to "All products (excl. gift cards)" | ✅
Configuring discounts apply to only "gift cards" | ✅
Configuring "favorite" discounts | ❌
Configuring "employee" discounts | ❌
Restricting redemption dates | ❌
Usage limit types other than `Per code` | ❌
Additional booking rules | ❌
Setting to "Allow multiple uses of a code in the same booking" | ❌

> Additional configuration detail can be found by using [**get discounts**](https://docs.roller.app/docs/roller-api/56d02d8498025) via our Data API.

## How do I get all codes for a discount?

Use [**get discounts**](https://docs.roller.app/docs/roller-api/56d02d8498025) via our Data API.

<!-- theme: warning -->
> The data API is not to be used for realtime scenarios. It's recommended discounts are cached on a daily basis or called infrequently.

---

## How do I validate codes in realtime?

Use the [**booking costs**](https://docs.roller.app/docs/rest-api/62e21c34b7ef3) endpoint.

---

## What happens when adding new codes to an existing discount?

When using [**update discount**](https://docs.roller.app/docs/rest-api/cvm27qdwoqjk2) all codes are additional to existing codes - they do not replace existing codes. 
Codes can only be removed via [**delete discount codes**](https://docs.roller.app/docs/rest-api/kd4qopxryu3cs).

> When codes are batch uploaded to a discount manually via Venue Manager, **this will overwrite all existing codes**.