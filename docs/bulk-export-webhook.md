---
stoplight-id: qg14o9szv8d26
---

# Bulk Export Webhook

> [**Create**](https://docs.roller.app/docs/api/rest/operations/create-webhook), [**view**](https://docs.roller.app/docs/api/rest/operations/get-webhooks) and [**delete**](https://docs.roller.app/docs/api/rest/operations/delete-webhook) webhooks using our REST API.

## Payload

The endpoint at the specified URL will receive a [**webhook message definition**](../models/WebhookMessageDefinition.yaml) with a [**bulk data export payload**](bulk-exports-overview.md) under the `data` object.

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
