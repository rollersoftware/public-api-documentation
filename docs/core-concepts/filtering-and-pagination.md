---
stoplight-id: r6w15c52hwcox
---

# Filtering and Pagination [Data API]

## Modified date

Depending on the type and quantity of data, endpoints are either filtered by the **modified date** of the record or provide all available data with no ability to filter records further. When a new record is created, the **modified date** is initially set from the **created date** of the record.

> When an existing record is modified, this updates the modified date of the record. This means that if you are returned data you already have (based on the unique identifier of the record), then **you need to update** (delete and replace) the existing data you have stored for that record.

- Date-filtered endpoints require a `startDate` and `endDate` query parameter, based on **venue local date-time**.
- Maximum query ranges **must not exceed** 1 day (24 hours).
- See the [**Formatting**](formatting.md) page for more information.

<!-- theme: warning -->
> The [**Get revenue entries**](../../reference/data-api.yaml#/paths/~1reporting~1revenue-entries/get) endpoint is an exception and **does not** filter based on modified date — it filters based on the **event date**.
>
> Booking records can be updated without any change to the event date. Records for bookings can occur over multiple dates, and individual records are **never modified**, so you should not clear out stored records (unless you are calling data for a date you previously stored data for).
>
> We recommend simply calling all data for the previous day each morning and storing it as additional records in your external table, repeating that process each morning.

## Pagination

If there is more data than the allowed `pageSize`, you need to page through the results.

By default, most endpoints return `100` records per page. You can change the number of records on a per-request basis by passing the `pageSize` parameter in the request URL.

When the response exceeds the `pageSize`, you can paginate through the records by incrementing the `pageNumber` parameter. We recommend beginning a series of calls to an endpoint by specifying `pageNumber` as `1`, then only making subsequent calls for additional pages if the number of pages returned is greater than 1.
