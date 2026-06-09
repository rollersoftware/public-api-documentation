---
stoplight-id: qg14o9szv8d26
---

# Bulk Export Webhook

> [**Create**](../../../reference/rest-api.yaml#/paths/~1webhooks/post), [**view**](../../../reference/rest-api.yaml#/paths/~1webhooks/get) and [**delete**](../../../reference/rest-api.yaml#/paths/~1webhooks~1{webhookId}/delete) webhooks using our Rest API.

## Payload

The endpoint at the specified URL will receive a [**webhook message definition**](../../../models/WebhookMessageDefinition.yaml) with a [**bulk data export payload**](https://docs.roller.app/docs/bulk-exports/407cs5vvmjb16) under the `data` object.

---

## Event types

The following are events compatible with the bulk  export webhook

| Enum      | ID  | Description                                                              |
| --------- | --- | ------------------------------------------------------------------------ |
| `Created` | `1` | Export request has completed and generated files are ready for download. |

---

## Optional Filters

None.

---

## Optional Fields

None.
