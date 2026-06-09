---
stoplight-id: vynaklh7qg8d1
---

# Signed Waiver Webhook

> [**Create**](../../../reference/rest-api.yaml#/paths/~1webhooks/post), [**view**](../../../reference/rest-api.yaml#/paths/~1webhooks/get) and [**delete**](../../../reference/rest-api.yaml#/paths/~1webhooks~1{webhookId}/delete) webhooks using our Rest API.

## Payload

The endpoint at the specified URL will receive a [**webhook message definition**](../../../models/WebhookMessageDefinition.yaml) with a [**signed waivers payload**](../../../models/SignedWaivers.yaml) under the `data` object. This will include the **adult** and **minor** signed waiver records in one flattened list.

---

## Event types

The following are events compatible with the signed waiver webhook

Enum | ID | Description
-|-|-
`Created`|`1`|A new **adult** waiver (including any associated **minors**) has been signed. 

---
