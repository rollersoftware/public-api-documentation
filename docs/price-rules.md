# Price Rules

A price rule dynamically changes ticket prices based on demand, timing, and purchase conditions. Including : 
- Quantity: Number of tickets purchased.
- Time: Day and time of the scheduled visit.
- Early-bird: How far in advance the booking is made.
- Capacity: Remaining availability for the session.

## Available price rule endpoints

- REST API > [**Get product detail**](https://docs.roller.app/docs/api/rest/operations/get-product-detail) (which products have a rule, and the prices each ticket type charges)
- REST API > [**Get price rules**](https://docs.roller.app/docs/api/rest/operations/get-price-rules) (the tiers of a `time` rule and when each one applies)
- REST API > [**Booking costs**](https://docs.roller.app/docs/api/rest/operations/get-booking-costs) (the authoritative price of a draft booking)

> Price rule configuration changes infrequently. Cache the responses of **Get product detail** and **Get price rules** rather than calling them on every checkout.

## How the data fits together

[**Get product detail**](https://docs.roller.app/docs/api/rest/operations/get-product-detail) returns two properties for price rules:

- `priceRuleId` on the parent product identifies the rule applied to the product. It is omitted when the product has no rule.
- `priceRule` on each ticket type in `products` holds the prices that ticket type charges under the rule. It has a `type` and one list of prices for that type. The other lists are omitted.

| `type` | Prices returned on the ticket type | Also needs **Get price rules**? |
|---|---|---|
| `quantity` | `quantityBrackets` and `quantityCalculation` | ❌ |
| `earlyBird` | `earlyBirdBrackets` | ❌ |
| `capacity` | `capacityBrackets` | ❌ |
| `time` | `timeTiers` | ✅ |

A `time` rule only lists a price per `tierId` on the ticket type. The name of each tier, and the days, times and dates it applies to, are shared by every product using the rule and are returned once by [**Get price rules**](https://docs.roller.app/docs/api/rest/operations/get-price-rules). Join the two responses on `priceRuleId`, then match `timeTiers[].tierId` to `timeRule.tiers[].tierId`.

## Brackets

`quantity`, `earlyBird` and `capacity` rules use brackets. Each bracket has an inclusive `from` and `to`, and the `price` charged when the value falls in that range. A `to` of `0` on the last bracket means the range has no upper bound.

```json
"priceRule": {
  "priceRuleId": "22f29d68-1c94-4de2-b616-020108d92a06",
  "type": "quantity",
  "quantityCalculation": "perProduct",
  "quantityBrackets": [
    { "from": 1, "to": 3, "price": 25 },
    { "from": 4, "to": 9, "price": 22 },
    { "from": 10, "to": 0, "price": 20 }
  ]
}
```

If no bracket matches, the ticket type's base `price` is charged.

### Quantity

The quantity is the total quantity of items on the booking with the same booking date and session. `quantityCalculation` determines what is counted:

- `perProduct` totals every ticket type of the parent product. e.g. `2` x Adult and `2` x Child count as `4`.
- `perVariation` totals only this ticket type. e.g. `2` x Adult and `2` x Child count as `2` for each.

### Early bird

The value is the number of whole days between the date the booking is made and the booking date. A bracket with `from` and `to` both `0` is the price for booking on the day. Anything at or beyond the `from` of the last bracket is charged the last bracket's price.

### Capacity

The value is the percentage of capacity remaining for the session, so `from` and `to` are percentages. e.g. `{ "from": 0, "to": 50, "price": 30 }` applies when half or less of the capacity remains.

## Time rules

A `time` rule has a list of named `tiers`. The first tier is the base price tier and has an empty `name`. Every other tier is a named variation such as `Peak`. The rule then describes when each tier applies:

- `recurring` lists the tier for each day of the week. Each day can list `times` of day that use a different tier to the rest of the day.
- `overrideDates` lists named date ranges that take precedence over `recurring`, such as school holidays. Each override has a `tierId` for the whole range and can list `days` of the week within the range that use a different tier, again with optional `times`.

Times of day are integers in 24h `Hmm` format: `900` is 9:00 AM and `1730` is 5:30 PM. A time range includes its `startTime` and excludes its `endTime`.

```json
[
  {
    "priceRuleId": "22f29d68-1c94-4de2-b616-020108d92a06",
    "name": "Peak and off peak",
    "type": "time",
    "timeRule": {
      "tiers": [
        { "tierId": "1", "name": "" },
        { "tierId": "2", "name": "Peak" }
      ],
      "recurring": [
        { "dayOfWeek": "sunday", "tierId": "2", "times": [] },
        { "dayOfWeek": "monday", "tierId": "1", "times": [] },
        { "dayOfWeek": "tuesday", "tierId": "1", "times": [] },
        { "dayOfWeek": "wednesday", "tierId": "1", "times": [] },
        { "dayOfWeek": "thursday", "tierId": "1", "times": [] },
        {
          "dayOfWeek": "friday",
          "tierId": "1",
          "times": [
            { "tierId": "2", "startTime": 1700, "endTime": 2100 }
          ]
        },
        { "dayOfWeek": "saturday", "tierId": "2", "times": [] }
      ],
      "overrideDates": [
        {
          "name": "School holidays",
          "tierId": "2",
          "dates": [
            { "startDate": "2026-12-19", "endDate": "2027-01-24" }
          ],
          "days": [
            { "dayOfWeek": "monday", "tierId": "1", "times": [] }
          ]
        }
      ]
    }
  }
]
```

The matching ticket type from **Get product detail** lists a price per tier:

```json
"priceRule": {
  "priceRuleId": "22f29d68-1c94-4de2-b616-020108d92a06",
  "type": "time",
  "timeTiers": [
    { "tierId": "1", "price": 25 },
    { "tierId": "2", "price": 32 }
  ]
}
```

### Which tier applies

To find the tier for a booking date and session start time:

1. Find the first override in `overrideDates` whose `dates` contain the booking date. If one matches, start with its `tierId`. If its `days` contain the booking's day of the week, use that day's `tierId` instead, or the `tierId` of the entry in that day's `times` that contains the session start time.
2. If no override matches, find the booking's day of the week in `recurring`. Use its `tierId`, or the `tierId` of the entry in its `times` that contains the session start time.
3. Look up the tier in the ticket type's `timeTiers`. If the tier has no entry, the base `price` applies.

Products without session times use the day's `tierId` and ignore `times`.

Using the example above, an Adult ticket is charged:

| Booking | Tier | Price |
|---|---|---|
| Wednesday 10 June 2026, 10:00 | `1` (recurring Wednesday) | `25` |
| Friday 12 June 2026, 18:00 | `2` (Friday `times` 17:00–21:00) | `32` |
| Friday 12 June 2026, 14:00 | `1` (recurring Friday, outside `times`) | `25` |
| Wednesday 23 December 2026, 10:00 | `2` (School holidays override) | `32` |
| Monday 21 December 2026, 10:00 | `1` (School holidays override, Monday exception) | `25` |

## Confirming the price

The price a guest will pay is always calculated by ROLLER. Before taking payment, call [**Booking costs**](https://docs.roller.app/docs/api/rest/operations/get-booking-costs) with the draft booking and use the returned item costs. Use the price rule configuration for display only.
