---
stoplight-id: nsncpipa2ghoi
---

# Formatting

## Date format

ROLLER APIs use the **ISO 8601** format (`yyyy-MM-dd` or `yyyy-MM-ddTHH:mm:ss`):

1. All returned date-time fields **without** a timestamp refer to the **venue local date-time**.
2. All returned date-time fields **with** a timestamp refer to **UTC**.

ISO 8601 provides precision and global compatibility, but it **does not represent the venue's local time** by default. You must convert all ISO 8601 values to the **venue's time zone** for local use.

> #### ISO 8601 example
> If a venue last modifies a booking on **15 Jul 2025 at 9:00 AM AEST (local time)**, then to query for this record using the Reporting API, use the venue local date-time:
> - `startDate` = `2025-07-15`
> - `endDate` = `2025-07-16`
>
> And where fields are returned with date-times:
> - `2025-07-15` would be in **venue local date-time**
> - `2025-07-14T23:00:00Z` would be in **UTC**

## Time zone of retrieved date-times

By default, all dates and times in the Reporting API (and Bulk Export API) are in UTC, unless the following **optional header** is specified, after which the venue time zone is used instead:

- **Header**: `TimeZone-Designators`
- **Value**: `offset`

This does not affect the date range parameters `startDate` or `endDate`, which are always in the venue time zone.

## Media types

ROLLER APIs support only the `application/json` format. You must include both of the following headers in your requests. Use `UTF-8` for all content encoding.

<!-- theme: success -->
> - **Content-Type:** `application/json; charset=UTF-8`
> - **Accept:** `application/json`
