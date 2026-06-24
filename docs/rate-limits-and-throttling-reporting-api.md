---
stoplight-id: 0cfnlry8rdx2k
---

# Rate Limits & Throttling [Reporting API]

<!-- theme: warning -->
> The Reporting API is **read-only** and not intended for real-time use cases.

The Reporting API does not support querying individual records. Instead, it provides **paginated exports** based on a record's **modified date**, which is ideal for **daily batch exports**. This lets you retrieve both new and updated records in a single call for syncing with external systems such as enterprise data warehouses or analytics platforms.

## Rate & call limits

### Rate limit

- Each API credential set is restricted to **120 requests per 60 seconds**.
- A **60-second cooling-off period** applies as a penalty if this is exceeded.

<!-- theme: warning -->
> Avoid sharing the same credentials across multiple applications, as it may trigger `429 Too Many Requests` errors.

### Call frequency recommendations

- Requests to the Reporting API should be made no more frequently than once a day.
- We recommend making calls outside business hours — for example, anywhere between `01:00` and `07:00` (for the previous day).

> For [**Get revenue entries**](https://docs.roller.app/docs/api/reporting/operations/get-revenue-entries), the default page size is 100 and cannot be adjusted.

### Monthly call limit

- Your monthly call limit is governed by your **ROLLER agreement** or API access **add-on plan**.
- Exceeding limits may lead to **additional charges** or **suspension** of access.
- API usage stats per endpoint are viewable in **Venue Manager > Settings > Integrations > API keys**.

---

## Bulk Exports

### Rate limit

* You are limited to **one request every 6 hours**, per `exportType`, per venue.
* There is no limit on date range.

<!-- theme: warning -->
> * This rate limit is enforced and will result in a `429 Too Many Requests` response if ignored.

### API usage

API usage is calculated depending on the size and date range of the request:

* `1 usage` per 10,000 records, per calendar month.

> #### Usage Examples
> * A request from `2020/01/01` to `2020/04/01` spans 3 calendar months, and returns `1` record per month
>   * This would count as `3 uses`
> ---
> * A request from `2020/01/28` to `2020/03/5` spans 3 calendar months, and returns `25,000` records per month
>   * This would count as `9 uses`
> ---
> * A request from `2020/04/10` to `2020/05/10` spans 2 calendar months, and returns `600` and `0` records for **APR**, **MAY** respectively
>   * This would count as `1 use`

### Monthly call limit

- This is governed by your **ROLLER agreement** or API access **Add-On plan**.
- Exceeding limits may lead to **additional charges** or **suspension** of access.
- API usage stats per endpoint are viewable via `Venue Manager > Settings > Integrations > API Keys`.
