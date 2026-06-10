---
stoplight-id: 7gn4zuznopwes
---

# Payment Link Webhook

> [**Create**](../reference/rest-api.yaml), [**view**](../reference/rest-api.yaml) and [**delete**](../reference/rest-api.yaml) webhooks using our Rest API.

## Payload

The endpoint at the specified URL will receive a [**webhook message definition**](../models/WebhookMessageDefinition.yaml) with a [**payment link payload**](../models/PaymentLink.yaml) under the `data` object.

---

## Event types

The following are events compatible with the payment link webhook

Enum | ID | Description
-|-|-
`Created`|`1`|A new payment link has been created (does not include draft bookings).
`Updated`|`2`|An existing payment link has recorded a payment against it
`Cancelled`|`3`|An existing payment link has been cancelled

---

## Important notes


* Payment links **can** be generated for bookings created via both API, and via ROLLER applications.
* Payment links **cannot** be created for API-draft, or venue-draft bookings.
* To see delivery status of issued payment links, please see the activity log on the relevant booking in VM.
* Only specify one contact detail - If both `email` and `phone` is provided, `email` will be ignored and only an SMS will be sent.
* Sending payment links to a recipient `phone` (via SMS) is unsupported in **Playground**.  
* Sending payment links will not create a guest record of the recipient, or attach them to the booking in VM.

## Alternatives

`Updated` events on the [**booking webhook**](booking-webhook.md) can also be subscribed to, for understanding remaining payment amounts on bookings which can be used to achieve similar outcomes.
