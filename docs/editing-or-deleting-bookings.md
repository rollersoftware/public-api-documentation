---
stoplight-id: p1hl65q4xzh0a
---

# Editing or Deleting Bookings

Bookings that have been created via the API can be adjusted, cancelled, or deleted via the API.

## Editing a booking

Adjust bookings using the [**Update a booking**](../reference/rest-api.yaml) endpoint. This method only allows you to add or remove products, with associated quantities, to or from the booking.

> If you wish to adjust the quantity, date, or another property of an existing item, remove that item and re-add it with the adjusted property.

## Cancelling a booking

Cancel bookings using the [**Cancel a booking**](../reference/rest-api.yaml) endpoint, and optionally add a refund as a payment record in ROLLER.

> - Only bookings created via the API can be cancelled via the API.
> - You can only cancel future bookings.
> - Cancelled bookings are still visible on some pages in Venue Manager.
> - Any associated payment records are still present for cancelled bookings.
> - Refunds must be processed outside of ROLLER — only a record of the refund can be added via the API.

## Deleting a booking

Delete bookings using the [**Delete a booking**](../reference/rest-api.yaml) endpoint, along with all associated transaction records.

> - You can only delete bookings you've made via the API.
> - You can only delete future bookings.
> - Cancelled bookings cannot be deleted.
> - All records of the booking are deleted from all ROLLER reports.

<!-- theme: warning -->
> If you still wish to retain any information about the booking, cancel it rather than delete it.
