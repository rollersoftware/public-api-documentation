---
stoplight-id: dhkft63bountn
---

# Postman Collection

Postman is an API client for testing endpoints, and our Collection ships every ROLLER endpoint pre-configured with the right paths, schemas, and auth flow - ready to send.

**Get set up**

1. Download [**Postman**](https://www.postman.com/) and launch it
2. From the top-left menu, choose **File > Import...**
3. Drop in the ROLLER collection which includes all Public API's, available [**here**](https://drive.google.com/file/d/1-4rhEEpjIckVidAbsziXzm34fOgRCeU8/view?usp=sharing)

> **Authenticate and start calling**
>
> 1. Open the collection's **Variables** tab
> 2. Paste your API credentials into the **Current Value** column, and adjust the environment variable if you're not on the default
> 3. Send the **Auth Token** request to retrieve a token
> 4. Copy the token into the **Token** variable's Current Value, prefixed with `Bearer ` (e.g. `Bearer xxxxxxxxx`) (A script to automate this process is also available in the collection)
> 5. Every other request in the collection will now authenticate automatically