---
stoplight-id: 501c2cc6476da
---

# Authentication

ROLLER API's use an OAuth2 flow whereby the consuming app uses their `client_id` and `client_secret` (generated in ROLLER Venue Manager) to request an access token from the `/token` endpoint.

### Getting access and generating credentials

See [**getting API access**](GettingApiAccess.md).


### Requesting an access token

To obtain an access token for the client credentials flow:

- **URL**: `https://api.roller.app/token` (See [**environments**](Environments.md))
- **HTTP Method**: `POST`
- **Content-Type**: `application/json`
- **Body** - `{"client_id":"xxxxxxxxxxxxxx","client_secret":"xxxxxxxxxxxxxxx"}`

Which should return a bearer token as per the example below:

```json
{
    "access_token": "cd5c24313225bb9ea046a2ef0f0dbb9f...",
    "token_type": "Bearer",
    "expires_in": 86400
}
```

### Making a request with the token

Once you have a token, a request must include the following:

* **Auth Type**: `OAuth 2.0`
* **Accept**: `application/json`
* **Authorization (Header)**: `Bearer cd5c24313225bb9ea046a2ef0f0dbb9f...`

> To avoid `429 (Too Many Requests)` we recommend calling the token endpoint once and storing the token in a central place such as a database.  For performance reasons you may wish to cache the token in your servers too, which means if you have multiple servers you must avoid each one making its own token request.

### Expiry

The access token is short-lived - its expiry is provided in the token response and may change, however it will generally be **24 hours**. Therefore consumer apps should always reuse the current token until they receive a 401 (Unauthorised) response from any endpoint at which time they should request a new token. 

<!-- theme: warning -->

>Do not request a new token for each API call. This may result in a 429 (Too many requests) response and result in the suspension of your API credentials/access.

### Scope

The scope of a set of API credentials (`client_id` and `client_secret`) is limited to a single venue, per environment. For example if you have multiple ROLLER venues you must create separate sets of credentials for each venue, and credentials generated in the Playground environment will not work in Production.


