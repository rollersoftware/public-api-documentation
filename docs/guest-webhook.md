---
stoplight-id: c9f31wv1iiubf
---

# Guest Webhook

> [**Create**](https://docs.roller.app/docs/api/rest/operations/create-webhook), [**view**](https://docs.roller.app/docs/api/rest/operations/get-webhooks) and [**delete**](https://docs.roller.app/docs/api/rest/operations/delete-webhook) webhooks using our REST API.

## Payload

The endpoint at the specified URL will receive a [**webhook message definition**](../models/WebhookMessageDefinition.yaml) with a [**guest payload**](../models/CustomerDetail.yaml) under the `data` object.

---

## Event types

The following are events compatible with the guest webhook

Enum | ID | Description
-|-|-
`Created`|`1`|A new guest is created
`Updated`|`2`|An existing guest is updated with new information.

>#### Actions that create a booking `Updated` event
>* Changes to any guest details.
>* When additional purchases have been made by the guest.
>* When the guest is deleted.

---

## Optional Filters

None.

---

## Optional Fields

The following fields will only be returned in the [**guest payload**](../models/CustomerDetail.yaml) if their corresponding value in the `include` object is `true`:

* [**Guest Flags**](../models/CustomerFlag.yaml)

View the [**create**](https://docs.roller.app/docs/api/rest/operations/create-webhook) webhooks endpoint for more detail.
