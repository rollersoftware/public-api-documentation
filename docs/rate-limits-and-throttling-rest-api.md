---
stoplight-id: ijcp98ygumj0w
---

# Rate Limits & Throttling [Rest API]

## Rate limit

- Each API credential set is restricted to **600 requests per 60 seconds**.
- A **60-second cooling-off period** applies as a penalty if this is exceeded.

<!-- theme: warning -->
> Avoid sharing the same credentials across multiple applications, as it may trigger `429 Too Many Requests` errors.

## Monthly call limit

- Your monthly call limit is governed by your **ROLLER agreement** or API access **add-on plan**.
- Exceeding limits may lead to **additional charges** or **suspension** of access.
- API usage stats per endpoint are viewable in **Venue Manager > Settings > Integrations > API keys**.
