---
stoplight-id: qc5cvegxcl1cy
---

# Getting API Access

> **If you're an existing ROLLER customer without the API access add-on:**
>
> Reach out to your Client Success Manager or contact [**ROLLER Support**](https://support.roller.software/hc/en-us/articles/115001690793-Contacting-ROLLER-Support-).
>
> **If you're not currently a ROLLER customer:**
>
> Get in touch with us via our [**Contact page**](https://www.roller.software/get-started/).

## Generate a ROLLER API key

1. Log in to [**Venue Manager**](https://manage.roller.app/).
2. Navigate to **Settings > Integrations > API keys**.
3. Click **Create client key**.
4. Enter a description in **Client key name** that best describes the consumer app or purpose the key will be used for — for example, `External Data Warehouse`.
5. Click **Create**.

## Restricted endpoints

Some REST API endpoints are restricted. They aren't included when you give an API key access to **All unrestricted endpoints**, and you can't add them to an API key yourself. ROLLER must enable them for each API key.

Restricted endpoints are currently those that:

- create, update, cancel or delete bookings, including draft bookings
- add payments, tips or payment links to a booking
- reserve or block capacity
- create or update modifier groups
- manage staff

Each restricted endpoint is marked on its page in this documentation. In Venue Manager, they're shown with a lock icon under **Restricted endpoints** when you update an API key's scope.

Requests to a restricted endpoint from an API key without access return `403 Forbidden` with the error code `INSUFFICIENT_SCOPE`.

### Request access to restricted endpoints

Contact our [**support team**](https://support.roller.software/hc/en-us/articles/115001690793-Contacting-ROLLER-Support-) and include:

- the **Client ID** of the API key
- the endpoints you need access to

> **Just getting started?**
>
> We recommend using the ROLLER **Playground** environment to test and set up your integrations before using the Live environment. The steps for generating credentials above are the same in Playground.
>
> Read more on the [**Environments**](environments.md) page.
