---
stoplight-id: 8yttl7sipu1uo
---

# Managing Staff via API

The staff API allows staff accounts belonging to a venue to be created, updated, and archived. This includes HQ venues and HQ controlled venues.

* **Venue staff** can be retrieved via the [**Get staff**](https://docs.roller.app/docs/api/reporting/operations/get-staff) endpoint in the Reporting API.
* **Venue staff roles** can be retrieved via the [**Get roles**](https://docs.roller.app/docs/api/reporting/operations/get-roles) endpoint in the Reporting API.

---

### Types of staff accounts

| State | `hasVerifiedEmail` | `isLocked` |
|-------------|-------------------|------------|
| Normal account (Active) | `true` | `false` |
| New normal account (Unverified email) | `false` | `true` |
| POS-only account (No email) | `false` | `false` |
| Locked account | `true` | `true` |

#### Staff users without an email (i.e. POS only staff)

Venue staff must be created or updated with **at least one** of `email`, or `posPin`. It is possible to create staff without emails in the instance they may not have one and/or do not require access to any other ROLLER applications, or do not require management access on POS.

#### Locked accounts

Staff accounts can be locked via API to prevent login to ROLLER applications, without requiring deletion of the account. More below.

Field | Detail 
---------|----------
`isLocked` | **The account is blocked from logging into ROLLER apps**. If the user has a verified email, the account is locked and is unable to login to any ROLLER applications using either email/password and/or POS PIN.
`hasVerifiedEmail` | **The account is unverified**. The user has not accepted the email invitation to set a password for their account (Does not apply for POS-only users without an email)

> **When viewing staff accounts in VM**
>
> Please note locked accounts cannot be edited via VM, you must use the API instead. Status meanings are below:
> Status | Description 
>---------|----------
> `Active` | Account is not locked and has a verified email
> `Locked` | Account is locked
> `Invite Sent: <dateTime>` | when not activated and invite timestamp exists 

---

### Creating staff

When creating a staff member:

1. When creating a staff member:
   - `hasVerifiedEmail = false`
   - `isLocked = true` when an email exists
   - `isLocked = false` for POS-only users
2. HQ access settings and `staffIdentities` are applied.

#### Email invitations

- If already activated → no-op success
- If not activated:
  - New activation code is generated
  - Invite timestamp is updated
  - Invitation email is sent
- Requires email-based account
- Sending an invitation does **not** unlock the account

---

### Updating staff

When updating a staff member:

1. Staff is loaded by `uniqueId` and venue access is verified.
2. Request is validated using create/update rules.

Staff accounts can be updated to include or remove `email` if required. If the **email changes**:
- Existing Auth0 user is deleted (if previously verified).
- Identity-provider linkage and invitation state are reset.
- `hasVerifiedEmail` becomes `false`.
- `isLocked` becomes `true`.

<!--theme: warning -->
>**Why this matters:**
>- Changing email creates a **new login lifecycle**.
>- The account must be **re-verified before it can be used**.
>- Prevents stale or unauthorized access tied to the old email.
>- Treat email changes as **identity resets** (re-invite + re-verify)

---

### Deleting staff

- Removes verified Auth0 identity linkage (if applicable)
- Removes associated `staffIdentities` contacts
- Deletes the staff account

---

### Locking staff accounts

- Sets `isLocked = true`.
- If the user has a verified email identity, the Auth0 account is blocked.
- **Prevents login via both email/password and POS PIN**.

Staff can only be unlocked if activated/verified.
- If not activated, unlock fails.
- If activated:
  - Account is unblocked (Auth0 where applicable)
  - `isLocked = false`

<!-- theme: warning -->
> **Note:** You cannot unlock a staff account if the email is not verified.

---

### HQ-only access controls

- `hqVenueGroupTags` and `hqVenueUniqueIds` are **HQ-only**.
- Non-HQ venues cannot set these fields, only set these fields in HQ venue contexts
- On HQ venues:
  - `hqVenueGroupTags` must be known HQ group tags.
  - `hqVenueUniqueIds` must be valid controlled venue unique IDs.
