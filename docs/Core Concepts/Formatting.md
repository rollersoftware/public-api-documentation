---
stoplight-id: nsncpipa2ghoi
---

# Formatting

## Date Format

1. ROLLER API's use the **ISO8601** format (`yyyy-MM-dd` or `yyyy-MM-ddTHH:mm:ss`)
2. All returned DateTime fields **without timestamps** refer to the **venue local DateTime**.
3. All returned DateTime fields **with timestamps** refer to **UTC**.

ISO8601 provides precision and global compatibility, but **does not represent the venue's local time** by default. You must convert all ISO8601 values to the **venue's timezone** for local use.

> #### ISO8601 Example
> If a venue last modifies a booking on **15 Jul 2025 at 9:00 AM AEST (Local Time)**, to query for this record using the Data API:
> - Use venue local DateTime:
>   - `startDate` = `2025-07-15`
>   - `endDate` = `2025-07-16`
> And where fields are returned with DateTimes:
> - `2025-07-15` would be in **venue local DateTime**
> - `2025-07-14T23:00:00Z` would be in **UTC**

## Time Zone of Retrieved DateTimes

By default all dates and times in DataAPI (And Bulk Export API) will be in UTC unless the following **optional header** is specified, after which the venue timezone will be used instead:

* Header: `TimeZone-Designators`
* Value: `offset`

Note: This does not affect the date range parameters `startDate` or `endDate` which are always in the venue timezone.

## Media Types

Our API's support only `application/json` format. You must include both of the following headers in your requests. `UTF-8` should be used for all content encoding.

<!-- theme: success -->
> - **Content-Type:** application/json; charset=UTF-8
> - **Accept:** application/json