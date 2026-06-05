---
stoplight-id: r6w15c52hwcox
---

# Filtering and Pagination [DataAPI]

## Modified Date
Depending on the type and quantity of data, endpoints will either be filtered by **modified date** of the record or provide all available data with no ability to further filter records. When a new record is created the **modified date** will initially set from the **created date** of the record. 

>When an existing record is modified, this will update the modified date of the record. This means that if you're returned data which you already have (based on the unique identifier of the record) then **you'll need to update** (delete and replace) the existing data you have stored for that record.

- Date filtered endpoints require a `startDate` and `endDate` query parameter based on **venue local DateTime**.
- Maximum query ranges **must not exceed** 1 day or 24 hours.
- See the [**formatting**](https://docs.roller.app/docs/roller-api/nsncpipa2ghoi) page for more information.

<!-- theme: warning -->
> The [**revenues entries endpoint**](https://docs.roller.app/docs/roller-api/5cc8264046482-get-revenue-entries) is an exception and **does not** filter based on modified date, it filters based on the **event date**. 
>
>Booking records can be updated without any change of the event date. Records for bookings can occur over multiple dates, and individual records will **never be modified**, so you should not clear out stored records (unless you're calling data for a date you previously stored data for). 
>
> It's recommended each morning to simply call all data for the previous day, and store it as additional records to your external table, repeating that process each morning.

## Pagination

If there's more data than the allowed `pageSize` you'll need to page through the results. 

By default, most endpoints return `100` records per page. You can change the number of records on a per-request basis by passing athe `pageSize` parameter in the request URL.

When the response exceeds the `pageSize`, you can paginate through the records by incrementing the `pageNumber` parameter. It's recommmended you begin a series of calls to an endpoint by specifying `pageNumber` as `1`, then only make subsequent calls for additional pages if the number of pages returned is greater than 1.