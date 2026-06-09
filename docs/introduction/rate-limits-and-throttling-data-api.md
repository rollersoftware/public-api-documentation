---
stoplight-id: 0cfnlry8rdx2k
---

# Rate Limits & Throttling [Data API]

<!-- theme: warning -->
> The ROLLER Data API is **read-only** and not intended for real-time use cases.

The Data API does not support querying individual records. Instead, it provides **paginated exports** based on a record's **modified date**, which is ideal for **daily batch exports**. This lets you retrieve both new and updated records in a single call for syncing with external systems such as enterprise data warehouses or analytics platforms.

## Rate & call limits

### Rate limit

- Each API credential set is restricted to **120 requests per 60 seconds**.
- A **60-second cooling-off period** applies as a penalty if this is exceeded.

<!-- theme: warning -->
> Avoid sharing the same credentials across multiple applications, as it may trigger `429 Too Many Requests` errors.

### Call frequency recommendations

- Requests to the Data API should be made no more frequently than once a day.
- We recommend making calls outside business hours — for example, anywhere between `01:00` and `07:00` (for the previous day).

> For [**Get revenue entries**](rate-limits-and-throttling-data-api.md), the default page size is 100 and cannot be adjusted.

### Monthly call limit

- Your monthly call limit is governed by your **ROLLER agreement** or API access **add-on plan**.
- Exceeding limits may lead to **additional charges** or **suspension** of access.
- API usage stats per endpoint are viewable in **Venue Manager > Settings > Integrations > API keys**.
