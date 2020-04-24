---
description: Frequently Asked Questions.
---

# 💬 FAQ

{% hint style="info" %}
Have a question that isn't answered here? Reach out to [**support@magic.link**](mailto:support@magic.link).
{% endhint %}

## How resilient is magic link delivery? Will users lose access to my service if Magic goes down?

Our platform team actively works to maintain and improve the stability and speed of our email delivery system. **We strive to ensure that magic links are delivered expediently and reliably at all times.**

In the unlikely event that Magic discontinues service in the future, users can **export their private key.** This is a key benefit of building on top of standardized public/private key cryptography. To ensure high availability and future-proofing, Magic is committed to pre-paying AWS infrastructure costs for several years so that our service runs _without interruption._

## Is there an option for Phone/SMS magic links, too?

Currently, we only offer email-based magic links. Due to [SIM swapping vulnerabilities](https://en.wikipedia.org/wiki/SIM_swap_scam), we do not support a Phone or SMS-based delivery mechanism. We understand this flexibility matters to you and your users, so we are constantly iterating and looking for ways to support Phone/SMS magic links in a secure way.

## What if a user loses access to their email?

If a user loses access to their email account, they need to contact their email service provider \(i.e.: Gmail, Microsoft Outlook, iCloud Mail\) and follow steps for account recovery.

## What if someone tries to phish users by sending a fraudulent magic link email?

[Phishing attacks](https://en.wikipedia.org/wiki/Phishing) are an ongoing problem that exists in our industry today. However, this doesn't mean we are sticking to the status quo; we are actively working on ways to mitigate this. We have minimized the attack vectors significantly by going passwordless—**no credentials are passed around!** Compared to traditional password-based solutions, Magic eliminates the case where users can be phished of compromising account information.

Plus, if a magic link email is lost or stolen \(or even somehow compromised in transit\), a user's account is safe! The token included in the magic link email is only privileged to verify a login request _from the device and/or browsing context that initiated the request._ An attacker would require physical access to the user's device _and_ unencrypted email inbox to be malicious.

However, a motivated attacker could create an identical replica of your application, which is a known phishing pattern that occurs today. For this case, we recommend developers to whitelist **specific domains for their Publishable API Keys on the** [**Magic Dashboard**](https://dashboard.magic.link) so that illegitimate applications cannot forge requests through the Magic SDKs.

## Is there a way to add custom Terms of Service \(TOS\) text to the magic link email?

Right now there isn't a way, but we are currently implementing a feature that enables developer to be able to completely customize the magic link email, and that will include being able to add your company-specific Terms of Service.

## How long does a user's authenticated session last with the Magic service?

Users remain authenticated with the Magic service for up to 7 days \(or until they clear their browser history/caches\). This means that a user will need to click on a magic link, at most, once every 7 days for each device they log into. We are exploring ways to allow this session length to be customizable via SDKs or the Magic Dashboard.

If you're building a custom backend, we recommend our [Decentralized ID token](tutorials/decentralized-id.md) as a way to initiate server-side sessions. The DID Token is a cryptographically-generated proof of user authentication. Your resource server simply needs to validate the token and set an HTTPS session cookie. This option gives you the flexibility of maintaining your own sessions without storing user secrets.

