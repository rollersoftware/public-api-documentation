---
stoplight-id: 1uypb6irt156u
---

# Overview

ROLLER offers two public APIs that serve different integration needs. Use this page to choose the right one for your use case, then follow the links in the sidebar for setup and reference detail.

>See our [**changelog**](changelog.md) for recent additions and changes.

## Reporting API

The Reporting API enables secure, structured access to your ROLLER data for integration with enterprise data warehouses, analytics platforms, and cloud storage solutions. It supports use cases like business intelligence, custom reporting, and data synchronization.

Key characteristics:

- The Reporting API is read-only. It does not provide the ability to write data to ROLLER, and it should not be used for real-time use cases, as it does not allow you to query specific records and instead returns paginated data for a time period only.
- It is optimised for the periodic export of records on a daily frequency.
- Available data is returned based on the modified date of the record, so both new and adjusted records are returned in the same call each day and can be updated in your external database.

## REST API

The REST API is a general-purpose API that supports real-time use cases and enables the creation of ROLLER bookings.

**[Use our Postman Collection to get started.](postman-collection.md)**

Key characteristics:

- Available products and capacities for specific dates can be called, and capacity can be reserved in advance of creating a booking.
- Bookings can then be created along with associated payments and customer records.
- Those bookings can be edited, cancelled, or deleted.
- Payments can be processed using the ROLLER Payments API. Alternatively, external payments can be recorded against existing bookings using the REST API.

The REST API also supports other use cases that draw on the available endpoints, for example:

- Searching for specific bookings based on booking IDs or other search criteria.
- Searching for guest details, or a list of bookings held by a specific guest.
- Viewing a list of available products, the dates and times they are available, and the capacity remaining on those dates and times.
