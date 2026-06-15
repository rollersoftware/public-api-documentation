---
stoplight-id: vpaprygcuft6t
---

# Associating Signed Waivers to Customers

A [**signed waiver**](../reference/reporting-api.yaml/paths/~1data~1signedwaivers/get) record has three important identifiers:

- **`SignedWaiverId`** – The unique identifier for that specific person's waiver record.
- **`ParentSignedWaiverId`** – The `SignedWaiverId` of the parent who signed on behalf of a minor.
- **`CustomerId`** – Ties to `CustomerId` in the Customers endpoint.

`ParentSignedWaiverId` is only returned for minors who have had their waiver signed by a parent. Each individual has their own signed waiver record, so a parent who signs on behalf of two minors returns three signed waiver records, which results in three unique customer records being created or updated.
