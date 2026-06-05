---
stoplight-id: ijcp98ygumj0w
---

# Rate Limits & Throttling [Rest API]

### **Rate Limit**
- Each API credential set is restricted to **600 requests per 60 seconds**, 
  - With a **60 second cooling off period** as a penalty if this is exceeded.

<!-- theme: warning -->
> Sharing the same credentials across multiple applications should be avoided as it may trigger `429 Too Many Requests` errors.

### **Monthly Call Limit**
- This is governed by your **ROLLER agreement** or API access **Add-On plan**.
- Exceeding limits may lead to **additional charges** or **suspension** of access.
- API usage stats per endpoint are viewable via `Venue Manager > Settings > Integrations > API Keys`.