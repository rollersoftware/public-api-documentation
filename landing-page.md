# ROLLER Developer Center

<!--theme:warning -->
> Please see the [**Changelog**](https://docs.roller.app/docs/roller-api/iglgjf34psufs) for all the latest updates.

Welcome! These API's enable you to connect your ROLLER venue across your software ecosystem — enabling real-time availability and booking workflows, data access, event-driven integrations and more.

**[Use our Postman Collection to get started](https://docs.roller.app/docs/roller-api/dhkft63bountn)**

- **Are you a ROLLER customer and venue operator?** → Head to [**Getting API Access**](#getting-api-access) below to find out how to generate your API keys and authenticate
- **Interested in becoming a ROLLER partner / integrator?** → Head to our [**Partner Directory**](https://www.roller.software/integration-partners/) to learn more
- **Just looking around?** → Read more about our available API's below, or access them in via left sidebar to get started

---
## Explore our API's

<!--
type: tab
title: REST API
-->

### ROLLER REST API
Best for **building real-time integrations and transactional workflows**.

**Use it to:**
- Retrieve products, sessions, and availability
- Create and manage real-time bookings in ROLLER
- Power your own external checkout or booking journey

Access here: **https://docs.roller.app/docs/rest-api**

<!--
type: tab
title: Data API
-->

### ROLLER Data API
Best for **analytics, reporting, and data warehousing**.

**Use it to:**
- Extract a copy of ROLLER data to your external database
- Feed BI tools and internal dashboards
- Support deeper performance analysis and automation

Access here: **https://docs.roller.app/docs/roller-api**

<!--
type: tab
title: Webhooks
-->

### ROLLER Webhooks
Best for **real‑time notifications** and event-driven systems.

**Use it to:**
- Subscribe to key events (e.g., booking changes)
- Receive payloads to your endpoint as events occur
- Keep external systems in sync without polling

Access here: **https://docs.roller.app/docs/webhooks**

<!--
type: tab
title: OCTO API
-->

### OCTO API
Best for **Online Travel Agent (OTA) resellers** and channel management providers looking to partner with ROLLER.

We officially support the **OCTO API Core** plus the **Pricing Capability** as part of our **Advanced Channel Management** feature.

- OCTO API Core: **https://docs.octo.travel/**
- Pricing Capability: **https://docs.octo.travel/capabilities-optional/pricing**

More information here: **https://www.roller.software/features/channel-management**

<!-- type: tab-end -->

---

## Other Resources

<!--theme:info -->
> **Need Help?** Visit the Help Centre for platform guidance and troubleshooting: **https://mysupport.roller.software/hc/en-us**

- **System status:** **https://status.roller.app/**
- **Academy (training):** **https://academy.roller.software/**
- **ROLLER Login:** **https://launchpad.roller.app**

---

## Getting API Access

<!--
type: tab
title: API Access
-->

### **If you are an existing ROLLER customer with the API access Add On:**

1. Login to ROLLER Venue Manager  
2. Navigate to **Settings > Integrations > API Keys**  
3. From the 'Select API' dropdown field at the bottom of the form, select ROLLER API and click the **Create API Client** button  
4. A pop-up window will be displayed, enter a description to the Client key name field which describes the consumer app that these credentials will be allocated to - such as _Data warehouse app_  
5. Click the **Create client key** button.

> **Don't have access?**
> * If you're an existing ROLLER customer without the API access Add On, please contact [**ROLLER Support**](https://mysupport.roller.software/hc/en-us) or your Client Success Manager
> * If you're not currently a ROLLER customer, please use get in touch via our website at **https://www.roller.software/get-started/**

<!--
type: tab
title: Authentication
-->

### Requesting an access token

ROLLER API's use an OAuth2 flow whereby the consuming app uses their client id and client secret to request an access token from the /token endpoint.

The Authorization header needs the **contentType** application/json, and the body includes the **client_id** and **client_secret** json payload.

To get an access token for the client credentials flow, you must do a POST to the API-URL/token endpoint:

- **URL**: `API_URL`/token  
- **HTTP Method**: POST  
- **Content-Type**: application/json  
- **Body**: {"client_id":"`YOUR_CLIENT_ID_HERE`","client_secret":"`YOUR_SECRET_HERE`"}

Which should return a bearer token as per the example below:

```json
{
  "access_token": "cd5c24313225bb9ea046a2ef0f0dbb9f",
  "expires_in": 86400,
  "token_type": "Bearer"
}
```

---

### Making a request with the token

The following is an example of retrieving [**product availability**](https://docs.roller.app/docs/rest-api/efb9788ea3808-get-product-availability) over a given date range:

- **URL**: `API_URL`/product-availability?date=2026-07-14
- **HTTP Method**: GET
- **Content-Type**: application/json  
- **Authorization**: Bearer cd5c24313225bb9ea046a2ef0f0dbb9f

---

### Scope

* The scope of a set of API credentials (client id and client secret) is limited to a single venue. 
* If you have multiple ROLLER venues you must create separate sets of credentials for each venue. 
* For more information regarding creating API credentials please see [**here**](https://docs.roller.app/docs/roller-api/qc5cvegxcl1cy).
* For more information on available environments please see [**here**](https://docs.roller.app/docs/roller-api/a9y16c1v2unac).

<!-- type: tab-end -->
