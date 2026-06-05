---
stoplight-id: p1hl65q4xzh0a
---

# Editing or deleting bookings

Bookings that have been created via the API can be adjusted, cancelled or deleted via the API.

### Editing a booking
Bookings can be adjusted using the [**update a booking**](https://docs.roller.app/docs/rest-api/branches/main/v4mzj4t4erwa9) endpoint. This method only allows you to add or remove products with associated quantities to or from the booking.
 
> If you wish to adjust the quantity, date or another property of an existing item, that item should be removed and re-added with the adjusted property.

---

### Cancelling a booking
Bookings can be cancelled using the [**cancel a booking**](https://docs.roller.app/docs/rest-api/branches/main/ymjdvd0uty55b) endpoint, and a refund optionally added as a payment record in ROLLER.

> - Only bookings created via API can be cancelled via API
> - You can only cancel future bookings
> - Cancelled bookings will still be visible in some pages in VM
> - Any associated payment records will still be present for cancelled bookings
> - Refunds must be processed externally of ROLLER - Only a record of the refund can be added via API.

---

### Deleting a booking

Bookings can be deleted using the [**delete a booking**](https://docs.roller.app/docs/rest-api/branches/main/t7x14rlu29wl4) endpoint, along with all associated transaction records.

> * You can only delete bookings you've made via the API
> * You can only delete future bookings
> * Cancelled bookings cannot be deleted
> * All records of the booking will be deleted from all ROLLER reports

<!-- theme: warning-->
> If you still wish to maintain any information about the booking it should be cancelled rather than deleted.
