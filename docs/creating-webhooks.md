---
stoplight-id: qxor5bzienbyu
---

# Creating Webhooks

To manage webhooks requires subscribing to events you wish to be notified about and which payload/s you wish to receive, using the webhook endpoints in the Rest API. 

You'll be required to specify a URL for ROLLER to send these notifications with a secure HTTPS endpoint. 

All webhooks are sent using HTTP POST.

All webhooks must respect the conditions outlined in [**retry logic and response handling**](retry-logic-and-response-handling.md).

Available webhook types can be found in the sidebar.

> API calls are required to create, edit, and delete webhooks, and these actions will count toward the call limit in your API package. However, receiving a webhook event does not count towards the limit.

---

## Rest API endpoints for managing webhooks

- [**Create webhooks**](../reference/rest-api.yaml)
- [**View existing webhooks**](../reference/rest-api.yaml)
- [**Update existing webhooks**](../reference/rest-api.yaml)
- [**Delete webhooks**](../reference/rest-api.yaml)

<!-- theme: warning -->
> Please note, deleted or disabled API keys do not currently delete or disable webhooks registered with that API key.

---

## IP addresses for allowlisting webhook traffic

Optional - The following IP addresses can be used to allowlist incoming webhooks sent by ROLLER:

### US Regions
* 54.152.123.222
* 54.89.85.224
* 18.213.198.255
* 35.168.0.202
* 3.227.97.165
* 52.23.29.216
* 54.213.241.3
* 35.165.9.182
* 52.42.20.181

### APAC Regions
* 13.55.197.161
* 13.239.148.90
* 13.238.71.16
* 13.238.178.159

### EMEA Regions
* 3.70.55.63
* 18.158.143.172
* 3.64.171.218
* 99.81.21.158
* 99.80.133.69
* 34.246.59.68

---
