---
stoplight-id: 501c2cc6476da
---

# Authentication

ROLLER APIs use an OAuth 2.0 flow, where the consuming app uses its `client_id` and `client_secret` (generated in ROLLER Venue Manager) to request an access token from the `/token` endpoint.

## Getting access and generating credentials

See [**Getting API Access**](getting-api-access.md).

## Requesting an access token

To obtain an access token using the client credentials flow, make the following request:

- **URL**: `https://api.roller.app/token` (see [**Environments**](environments.md))
- **HTTP method**: `POST`
- **Content-Type**: `application/json`
- **Body**: `{"client_id":"xxxxxxxxxxxxxx","client_secret":"xxxxxxxxxxxxxxx"}`

This returns a bearer token, as in the example below:

```json
{
    "access_token": "cd5c24313225bb9ea046a2ef0f0dbb9f...",
    "token_type": "Bearer",
    "expires_in": 86400
}
```

## Making a request with the token

Once you have a token, every request must include the following:

- **Auth type**: `OAuth 2.0`
- **Accept**: `application/json`
- **Authorization (header)**: `Bearer cd5c24313225bb9ea046a2ef0f0dbb9f...`

> To avoid `429 (Too Many Requests)`, we recommend calling the token endpoint once and storing the token in a central place such as a database. For performance, you may also wish to cache the token on your servers. If you have multiple servers, you must avoid each one making its own token request.

## Expiry

The access token is short-lived. Its expiry is provided in the token response and may change, but it is generally **24 hours**. Consumer apps should always reuse the current token until they receive a `401 (Unauthorised)` response from any endpoint, at which point they should request a new token.

<!-- theme: warning -->
> Do not request a new token for each API call. This may result in a `429 (Too Many Requests)` response and lead to the suspension of your API credentials and access.

## Scope

The scope of a set of API credentials (`client_id` and `client_secret`) is limited to a single venue, per environment. For example, if you have multiple ROLLER venues, you must create separate sets of credentials for each venue. Credentials generated in the Playground environment will not work in Production.
