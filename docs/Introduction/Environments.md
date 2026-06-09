---
stoplight-id: a9y16c1v2unac
---

# Environments

ROLLER provides two environments: Live and Playground. This page covers the base URLs for each and how to access Playground for testing.

> Base URLs may differ if you have a dedicated domain agreement.

## Live environment

<!-- theme: success -->
> #### Live base URL
> `https://api.roller.app`

## Playground environment

To ensure the smooth implementation and functionality of new integrations, we recommend using the Playground environment for initial testing rather than the Live environment.

<!-- theme: success -->
> #### Playground base URL
> `https://api.play.roller.app`

### Benefits of using Playground

- **Parity**: Playground runs on the same version as the Live environment, so it is an accurate sandbox representation of behaviour.
- **Scope safety**: Changes and tests carried out in Playground do not affect your live data, minimizing the risk of disruption to your operations. This enables isolated debugging, so you can identify and resolve issues without affecting real-time transactions or customer interactions.

### Accessing the Playground environment

1. Log in to ROLLER Venue Manager.
2. Select the **Your Account** icon at the bottom of the left-side menu.
3. Select **Switch to Playground venue**.
4. You are automatically redirected to your Playground account.

> Learn more about Playground in our [**help center**](https://support.roller.software/hc/en-us/articles/360000298275-ROLLER-Playground).

<!-- theme: warning -->
> While using Playground to generate and host API keys currently in use, do not click the **Update Playground** button in Venue Manager. This will irreversibly reset the Playground instance and you will lose access to those keys.
