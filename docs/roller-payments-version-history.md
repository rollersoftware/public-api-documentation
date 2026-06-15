---
stoplight-id: egj77d29eagwv
---

# Version History

As new payment library packages are released these should be updated in your implementation as soon as possible to ensure you get the latest features, updates to compliance and security, and support. See Adyen's offical release notes [**here**](https://docs.adyen.com/online-payments/release-notes/).

<!--theme: warning -->
> It's important to only implement ROLLER-approved package updates hosted here, as new versions may require implementation changes, and should be verified against the latest ROLLER documentation.

Release Date | Change | Package Version
-|-|-
2025/04/29 | - Updated `adyen-web` from `v5.65.0` to `v.5.71.2`<br>- Updates to meet `iDeal` payment method compliance<br>- Zip code is now always required for card payments through the Adyen drop-in component <br> - Support `AdyenPaymentMethod.googlepay` variant | v217 ([**download**](https://staging-cdn.rollerdigital.com/lib-ecom-payments/ecom-payments_v217.zip))
-/-/- | Initial Package | v146
