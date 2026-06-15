---
stoplight-id: zn5hys30vqord
---

# Retry Logic and Response Handling

## Introduction

Webhook interactions are a critical component in ensuring seamless data communication between ROLLER and third-party services. This section details our retry mechanisms and the acceptable response codes from third-party endpoints.

---

## Webhook Response Expectations

Upon receiving a webhook from ROLLER, third-party services are expected to quickly store or queue the request for processing outside the request context, without executing prolonged logic during receipt. This ensures timely and efficient handling.

### Performance Thresholds

- **Optimal Response Time:** Responses should ideally be acknowledged in under `1 second`.
- **Maximum Allowed Time:** Webhook requests must be acknowledged within `10 seconds` to avoid retries or deactivation.

### Event Ordering
ROLLER does not guarantee delivery of events in the order in which they are generated. For example, you might get a redemption event before the booking created event.

Your endpoint should not expect delivery of events in a specific order, and needs to handle delivery accordingly. You can also use the API to fetch any missing objects

---

## Retry Mechanisms

If a webhook delivery fails due to issues on either side, ROLLER employs a structured retry schedule:

- **First Attempt:** `Immediate`
- Scheduled Retries:
  - **Second Attempt:** `1 minute` after the first attempt.
  - **Third Attempt:** `1 minute` after the second attempt.
  - **Fourth Attempt:** `15 minutes` following the third attempt.
  - **Fifth Attempt:** `1 hour after` the fourth attempt.
  - **Sixth Attempt:** `1 day` after the fifth attempt.
  - **Seventh and Final Attempt:** `3 days` post the sixth attempt.

<!-- theme: warning -->

> If all seven attempts fail, the webhook is automatically disabled to maintain system stability and performance.

> #### Notifications for Failing Webhooks
>
> When a webhook reaches its sixth retry attempt, ROLLER will alert the venue's `Account Owner` and `Primary Contact`. This notification serves as a proactive measure, allowing the third-party sufficient time to address and resolve any issues before the webhook is disabled.
>
> [**Learn how to configure contact information**](https://support.roller.software/hc/en-us/articles/6674794303247-How-do-I-update-the-account-owner-primary-contact-billing-contact-and-technical-contact#question-0-0).

---

## Acceptable Response Codes

Third-party endpoints should return specific HTTP status codes to indicate the result of the webhook request handling:

- **200 OK:** Successfully processed the webhook request.
- **500 Internal Server Error:** Issue on the third-party's side; webhook will be retried according to the schedule.
- **503 Service Unavailable:** Temporary unavailability; retries will follow the specified schedule.
- **504 Gateway Timeout:** Indicates a timeout, which should be rare since our request window is 10 seconds. Retries will be scheduled regardless.

Responses with status codes outside the ones listed above will trigger an automatic review and potential deactivation of the webhook. This measure ensures that only compliant and responsive integrations remain active.

---

## Monitoring and Compliance

ROLLER continuously monitors the performance of webhook interactions. Persistent delays or non-compliance with response time thresholds will result in notifications to the third party and, if necessary, adjustments in the webhook's operational status.
