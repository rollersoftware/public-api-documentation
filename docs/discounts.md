---
stoplight-id: xy4jtgqlldj5o
---

# Discounts

The REST API allows you to create and update discount configurations, including adding or removing usable `codes` for a discount. This enables external discount management, which can be used in scenarios such as:

- Registering promotional codes created by a third party, such as those issued via email/SMS marketing or on pre-printed voucher/coupon stock.
- Automating the regular, manual bulk upload of discount codes.

<!-- theme: warning -->
> #### Unsupported scenarios
> Creating duplicate discount codes across several ROLLER platforms to enable multi-venue discounts is strongly discouraged due to the technical limitations it introduces. If you are interested in achieving this functionality, please get in touch to register your interest.

## Available discount endpoints

- Reporting API > [**Get discounts**](https://docs.roller.app/docs/api/reporting/operations/get-discounts)
- REST API > [**Get discount**](https://docs.roller.app/docs/api/rest/operations/get-discount)
- REST API > [**Update discount**](https://docs.roller.app/docs/api/rest/operations/update-discount)
- REST API > [**Create discount**](https://docs.roller.app/docs/api/rest/operations/create-discount)
- REST API > [**Create discount codes**](https://docs.roller.app/docs/api/rest/operations/create-discount-codes)
- REST API > [**Delete discount codes**](https://docs.roller.app/docs/api/rest/operations/delete-discount-codes)
- REST API > [**Booking costs**](https://docs.roller.app/docs/api/rest/operations/get-booking-costs) (for **discount code validation**)

## What discount configurations are currently supported?

Discount `codes` can be added to or removed from any discount in your venue. However, creating and updating discounts via the REST API can only be done with certain discount configurations:

| Configuration | Supported? |
|---|---|
| Percentage discounts | ✅ |
| Fixed amount discounts | ✅ |
| Buy & Get discounts | ❌ |
| Restricting booking dates | ✅ |
| Limitations per application (sales channel) | ✅ |
| `X` uses `Per code` limitations | ✅ |
| "Issue codes on purchase" discounts | ❌ |
| Configuring discounts to apply to "All products (excl. gift cards)" | ✅ |
| Configuring discounts to apply to only "gift cards" | ✅ |
| Configuring "favorite" discounts | ❌ |
| Configuring "employee" discounts | ❌ |
| Restricting redemption dates | ❌ |
| Usage limit types other than `Per code` | ❌ |
| Additional booking rules | ❌ |
| "Allow multiple uses of a code in the same booking" | ❌ |

> Additional configuration detail can be found using [**Get discounts**](https://docs.roller.app/docs/api/reporting/operations/get-discounts) via the Reporting API.

## How do I get all codes for a discount?

Use [**Get discounts**](https://docs.roller.app/docs/api/reporting/operations/get-discounts) via the Reporting API.

<!-- theme: warning -->
> The Reporting API is not to be used for real-time scenarios. We recommend that discounts are cached on a daily basis or called infrequently.

## How do I validate codes in real time?

Use the [**Booking costs**](https://docs.roller.app/docs/api/rest/operations/get-booking-costs) endpoint.

## What happens when I add new codes to an existing discount?

When using [**Update discount**](https://docs.roller.app/docs/api/rest/operations/update-discount), all codes are additional to existing codes — they do not replace them. Codes can only be removed via [**Delete discount codes**](https://docs.roller.app/docs/api/rest/operations/delete-discount-codes).

> When codes are batch uploaded to a discount manually via Venue Manager, **this overwrites all existing codes**.
