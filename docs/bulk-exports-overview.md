---
stoplight-id: 66otoe75x30hk
---

# Bulk Exports Overview

Bulk exports via API allows the ability to backfill historical ROLLER data from multiple days. This is done by submitting an export request, that once processed will notify webhook subscribers that it is ready for download.

## Steps to setup

1. [**Create a webhook**](creating-webhooks.md) with type **bulkExport** and subscribe to the `Created` event type
2. Use the [**bulk data export request endpoint**](https://docs.roller.app/docs/api/reporting/operations/bulk-data-export-request) to submit a new export request
3. Once the request has finished processing, you'll receive a [**bulk data export payload**](../models/BulkDataExportCompleted.yaml) via the webhook registered in step 1, containing presigned URL's hosting the requested data.

---

## What data can be exported in bulk?

The following `exportType`'s are supported:

* `RevenueEntries`
* `Customers`
* `Attendance`
* `Payments`
* `MembershipRedemptions`
* `MembershipStatuses`
* `MembershipCredits`
* `Tickets`
* `Giftcards`
* `BookingItems`
* `PosTillReconciliations`
* `SignedWaivers`
* `BookingSignedWaivers`

> The format of each export is the same as the corresponding export requests via the [**Reporting API**](../reference/reporting-api.yaml).

---

## Bulk export payload

The [**webhook message**](../models/WebhookMessageDefinition.yaml) will contain a [**bulk data export payload**](../models/BulkDataExportCompleted.yaml), for example:

```json
{
  "venueId": 3066,
  "preSignedUrls": [
    "https://roller-locala.s3.ap-southeast-2.amazonaws.com/bulk-exports/4-EbqmlvPZW0mA-ZVgfGrgGg-20240501-BookingItems.json"
  ],
  "exportType": "BookingItems",
  "processId": "EbqmlvPZW0mA-ZVgfGrgGg",
  "sequenceNumber": 1,
  "sequenceTotal": 6
}
```

## Understanding the response structure

#### Split data files
You may receive multiple presigned URL's for a single request, as files are split based on the number of records rather than specific time periods.

> Each file includes a suffix in the filename to denote its sequence. 
>
> * For example: `1288-X_ajWfL51kCazNvDiHR1Bw-20241218-BookingItems-1.json`

##### Sequenced responses

Where data spans several months, multiple webhooks will be sent in sequence, denoted by `sequenceNumber` and `sequenceTotal`. If a request date covers periods of inactivity, you will receive a webhook with no pre-signed URLs.
  * For example an export duration of 60 months (if the data is available) will send one webhook per month, each potentially containing a list of several presigned URLs to keep filesize manageable.

<!-- theme: warning -->
> #### Delay considerations
> * Data generation can take significant time depending on the size of the request.
> * You may receive data out of order, for example the data for March could come before the data for February.

##### Expiry

Presigned URL's are valid for 5 days, after which they will expire and cannot be used.
