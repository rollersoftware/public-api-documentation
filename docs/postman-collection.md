---
stoplight-id: dhkft63bountn
---

# Postman Collection

Postman is an API client for testing endpoints. Our collection ships every ROLLER endpoint pre-configured with the right paths, schemas, and auth flow — ready to send.

## Get set up

1. Download [**Postman**](https://www.postman.com/) and launch it.
2. From the top-left menu, choose **File > Import**.
3. Either:
   - Select **Link**, paste the URL below, and click **Continue**: `https://raw.githubusercontent.com/rollersoftware/public-api-documentation/main/reference/postman-collection.json`
   - Or [**download the collection file directly**](../reference/postman-collection.json) and import it from your file system.

## Authenticate and start calling

1. Open the collection's **Variables** tab.
2. Paste your `clientId` and `clientSecret` into the **Current value** column. Set `baseUrl` to `https://api.roller.app` if using production (the default is the sandbox environment).
3. Send the **Get OAuth token** request — it will automatically store your access token.
4. Every other request in the collection now authenticates automatically.
