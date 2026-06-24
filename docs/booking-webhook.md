---
stoplight-id: 1tjb4whgq33f0
---

# Booking Webhook

> [**Create**](https://docs.roller.app/docs/api/rest/operations/create-webhook), [**view**](https://docs.roller.app/docs/api/rest/operations/get-webhooks) and [**delete**](https://docs.roller.app/docs/api/rest/operations/delete-webhook) webhooks using our REST API.

## Payload

The endpoint at the specified URL will receive a [**webhook message definition**](../models/WebhookMessageDefinition.yaml) with a [**booking payload**](../models/BookingDetail.yaml) under the `data` object.

---

## Event types

The following are events compatible with the booking webhook:

Enum | ID | Description
-|-|-
`Created`|`1`|A new reserved booking is created (does not include draft bookings).
`Updated`|`2`|An existing booking is updated with new information such as changes to booking items, booking contacts, payments or refunds that are made, or adjustments to tickets. See more [**below**](#actions-that-create-a-booking-updated-event).
`Cancelled`|`3`|An existing booking is cancelled

> #### Actions that create a booking `Updated` event
> <br>
> <details><summary style="color: #0081CC; cursor: pointer;">&nbsp;<strong> Click to expand...</strong></summary>
> <br>
>
> #### Included actions ✅
> - Reserving a draft booking
> - Editing booking name
> - Editing booking holder (or company) attached to a booking
> - Adding booking contacts to a booking
> - Adding and removing items from a booking, varying item quantity
> - Changing booking date/time, or expiry date of booking items
> - Modifying assigned resources for booking items
> - Adding or refunding of any payments (Includes tips, complimentary bookings and marking invoices as paid)
> - Adding and removing discounts from a booking
> - Assigning and removing staff to the booking
> - Attaching waivers to a ticket on the booking
> - Changes to the status of any memberships in the booking
> - Editing ticket information such as ticket photo, ticket name, and custom ticket ID
> - Editing POS notes and VM Booking Notes
> - Adding and editing table number for the booking (via POS)
> - Adding forms, form responses and editing forms on bookings (Only those with databinding to `booking`)
> - Assigning and removing staff to the booking
> - Assigning or revoking Wallets, or editing Wallet details
> - Refunding Wallet balances
>
> #### Not included ❌
> - Creating a booking
> - Redeeming tickets on the booking
> - Attaching waivers to a booking (via unique waiver link)
> - Editing hold status for tentative bookings
> - Editing guest records attached to bookings (Either as a contact or booking holder)
> - Issuing and cancelling invoices for the booking, or payment links
> - Sending emails or logging calls against the booking
> - Sending confirmation emails or waiver requests
> - Printing tickets or receipts on the booking
> - Modifying amount, expiry, or details of giftcards on the booking
>
> *(All actions listed include both VM and POS where relevant unless specified otherwise)*
>
> </details>

---

## Optional Filters

Bookings that trigger this webhook can be specified by including the following objects in the `filter` object:

* Sales Channel (`channels`) — filter by the channel the booking was **created** in
* Event Channel (`eventChannels`) — filter by the application that **triggered the specific event**
* Product Type
* Product IDs
* Product Category

View the [**create**](https://docs.roller.app/docs/api/rest/operations/create-webhook) webhooks endpoint for more detail.

> Specifying filters is optional. If multiple filters are specified, the result will be the intersection of both filters. For example if specifying a `productId` and `productCategory` filter, the resulting product must belong to both.

### Sales Channel vs Event Channel

The `channels` and `eventChannels` filters serve different purposes:

| Filter | Filters on... | Use when... |
|---|---|---|
| `channels` | The channel the **booking was created in** | You only want events for bookings made at POS, or bookings made online |
| `eventChannels` | The application that **triggered this specific event** | You want to react to a specific action in a specific app, regardless of where the booking was originally created |

**Example:** A booking created online (`channels: [Consumer]`) can later be updated by a staff member at POS. Filtering by `eventChannels: [PointOfSale]` will deliver the `Updated` event for that action; filtering by `channels: [Consumer]` will not.

> Existing webhook subscriptions without an `eventChannels` filter continue to receive events from all applications — no changes are required to existing integrations.

---

## Optional Fields

The following fields will only be returned in the [**booking payload**](../models/BookingDetail.yaml) if their corresponding value in the `include` object is `true`:

* [**Membership Detail**](../models/MembershipDetail.yaml)
* [**Guest Flags**](../models/CustomerFlag.yaml)
* External ID
* Tickets
* Locations
* Payments
* Metadata

View the [**create**](https://docs.roller.app/docs/api/rest/operations/create-webhook) webhooks endpoint for more detail.

---

## Example

*"Get notified of all guest names every time a party booking is made at POS"*

**Example breakdown**:
- **Webhook**: Booking webhook
- **Event**: `Created`
- **Include**: `tickets`
- **Filters**: 
  - **Channel**: `POS`
  - **Product Category**: `Party Products`
    - This includes all products with this product category
    - eg: *Basic Party*, *Mega Party*, and *Epic Party*

**Request Body**:

<details> <summary>Click to expand</summary>

```json
{
    "url": "https://your-url-to-receive-webhook.com/12345",
    "enabled": "true",
    "authentication": {
        "apiKey": "CRM Trigger Webhook 002"
    },
    "webhooks": {
        "booking": {
            "events": [
                "Created"
            ],
            "include": {
                "tickets": true
            },
            "filter": {
                "channels": [
                    "doorlist"
                ],
                "productCategory": "Party Products"
            }
        }
    }
}
```

</details>

**Response**:

<details> <summary>Click to expand</summary>

```json
{
  ...
  "items": {
    "tickets": {
      "ticketHolderName": "Ben Smith",
      ...
    }
  }
}
```

</details>

> This example assumes that when these bookings are made at POS, that `ticketHolderName` is captured. Note: This field is automatically populated with a guest's name if waivers are attached to each ticket.
