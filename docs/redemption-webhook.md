---
stoplight-id: c9ntvneweithh
---

# Redemption Webhook

> [**Create**](../reference/rest-api.yaml/paths/~1webhooks/post), [**view**](../reference/rest-api.yaml/paths/~1webhooks/get) and [**delete**](../reference/rest-api.yaml/paths/~1webhooks~1{webhookId}/delete) webhooks using our REST API.

## Payload

The endpoint at the specified URL will receive a [**webhook message definition**](../models/WebhookMessageDefinition.yaml) with a [**redemption payload**](../models/RedemptionDetail.yaml) under the `data` object.

---

## Event types

The following are events compatible with the redemption webhook

Enum | ID | Description
-|-|-
`Created`|`1`|A ticket has been redeemed. You may receive multiple tickets in the redemption payload at once as ROLLER POS will batch send redemptions every 15 seconds.

<!-- theme: warning -->
> Please note, redeeming **stock** and **addon** type products do not trigger the redemption `Created` event and will not send a webhook. 

---

## Optional Filters

Bookings that trigger this webhook can be specified by including the following objects in the `filter` object:

* Product IDs
* Product Category

View the [**create**](../reference/rest-api.yaml/paths/~1webhooks/post) webhooks endpoint for more detail.

> Specifying filters is optional. If multiple filters are specified, the result will be the intersect of both filters. For example if specifying a `productId` and `productCategory` filter, the resulting product must belong to both.

---

## Optional Fields

The following fields will only be returned in the [**redemption payload**](../models/RedemptionDetail.yaml) if their corresponding value in the `include` object is `true`:

* [**Membership Detail**](../models/MembershipDetail.yaml)
* [**Multi-Pass Detail**](../models/MultiPass.yaml)

View the [**create**](../reference/rest-api.yaml/paths/~1webhooks/post) webhooks endpoint for more detail.
