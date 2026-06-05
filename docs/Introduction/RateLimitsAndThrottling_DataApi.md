---
stoplight-id: 0cfnlry8rdx2k
---

# Rate Limits & Throttling [Data API]

<!-- theme: warning -->
> The ROLLER Data API is **read-only** and not intended for real-time data use cases. 

The Data API does not support querying individual records but instead provides **paginated exports** based on a **record's modified date**, ideal for **daily batch exports**. This enables both new and updated records to be retrieved in a single call for syncing with external systems like enterprise data warehouses or analytics platforms.

## Rate & Call Limits

### **Rate Limit**
- Each API credential set is restricted to **120 requests per 60 seconds**, 
  - With a **60 second cooling off period** as a penalty if this is exceeded.

<!-- theme: warning -->
> Sharing the same credentials across multiple applications should be avoided as it may trigger `429 Too Many Requests` errors.

### **Call Frequency Recommendations**

- Requests to the Data API should not be more frequent than on a daily basis.
- Calls are reccommended to be made out of business hours, for example anywhere between `01:00` - `07:00` (for the previous day)

> For [**Get revenue entries**](https://docs.roller.app/docs/roller-api/5cc8264046482-get-revenue-entries), default page size is 100 and cannot be adjusted.

### **Monthly Call Limit**
- This is governed by your **ROLLER agreement** or API access **Add-On plan**.
- Exceeding limits may lead to **additional charges** or **suspension** of access.
- API usage stats per endpoint are viewable via `Venue Manager > Settings > Integrations > API Keys`.