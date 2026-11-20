# ToknShield Privacy Policy

Effective date: 20 November 2026 · Version 1.0 (beta)

ToknShield is provided by **Portfolioapp Pty Ltd** (ACN 688 794 247, ABN 74 688 794 247), Queensland, Australia. Contact: [tom@capinora.com](mailto:tom@capinora.com).

## 1. About ToknShield

ToknShield is a local-first privacy tool for ChatGPT. It has two parts:
- a Chrome extension
- a companion app for macOS

It looks for sensitive details, such as names, email addresses, phone numbers, addresses and account details. It replaces them with placeholders before your message or file is sent, and lets you restore the real details on your Mac.

Detection isn't perfect. ToknShield reduces the risk of sharing private details; it doesn't guarantee that every sensitive detail is found.

## 2. What happens on your device

When you use ToknShield, the extension and the Mac app may process:
- text you type
- documents you choose to protect, and their file names
- the sensitive values they find
- the placeholders that replace them

They do this on your Mac. The ToknShield extension and app make no network connections to Portfolioapp, and we run no servers that receive your messages, documents or detected values.

To restore the real details later, ToknShield keeps a mapping between placeholders and original values on your Mac. It's held in the macOS Keychain (this device only, readable while your Mac is unlocked) and in the app's local storage. The extension also keeps its settings, such as your protection mode, in Chrome's local storage. The app writes routine operational messages to the macOS system log on your Mac; these are not sent to us.

**What goes to ChatGPT.** When you attach a supported file through ToknShield, the original stays on your Mac and ChatGPT receives only the protected copy. Whatever you choose to send, including protected messages and files, is handled by OpenAI under its own terms and privacy policy.

**What ToknShield can't protect.** Files you pick from Google Drive, ChatGPT's Library or other connected apps are fetched by ChatGPT itself, so ToknShield can't protect them. For this beta, use made-up or non-sensitive files, and don't select private files from Drive or ChatGPT Library. When protection is switched Off, ChatGPT works normally and nothing is protected.

## 3. Information we collect

We collect only:
- **Beta sign-ups.** If you join the beta at toknshield.com, we store your email address and send you a welcome email. We also send ourselves a notification that includes your address.
- **Emails you send us.** If you contact us, we receive whatever you include. Please don't send real personal or client documents, unredacted screenshots or passwords.
- **Document counts.** The website may show how many documents beta testers have protected. This counter stores only random identifiers, not content, names or file details.

We don't use analytics or advertising tools, and ToknShield does not collect crash reports or diagnostics from your device.

## 4. Service providers

We use these providers to run the website, deliver email and distribute the beta:

| Provider | What it does | What it receives |
|---|---|---|
| OpenAI website hosting | Hosts toknshield.com and stores beta sign-ups | Your sign-up email address, and normal web request data such as IP address |
| Resend | Sends beta emails | Your sign-up email address and the email content |
| Cloudflare | Domain name service and site security for toknshield.com | Normal web request data such as IP address; sets one security cookie |
| GitHub | Hosts beta.toknshield.com and the beta downloads | Normal web request data such as IP address |

These providers may store or process data in the United States and other countries. We don't sell personal information, and we don't share it for advertising.

## 5. Cookies

toknshield.com sets one strictly necessary cookie, `__cf_bm`, from Cloudflare. It helps protect the site from automated abuse and expires after about 30 minutes. The site does not use analytics, advertising or tracking cookies. beta.toknshield.com does not set cookies. You can manage cookies in your browser settings.

## 6. How long we keep information

- **Beta sign-up email addresses:** kept while the beta runs and deleted within 12 months after it ends, or sooner if you ask.
- **Support emails:** kept only as long as needed to help you and keep a record of the request.
- **On your Mac:** ToknShield's data stays on your Mac until you remove it. The removal steps in the install guide delete the app and its Chrome registrations. Entries in the macOS Keychain may remain; you can delete ToknShield entries in Keychain Access.

## 7. Security

We use reasonable safeguards for the information we handle. No software can guarantee that it detects every sensitive detail, prevents every disclosure or works without interruption. See our [Security and Data Handling Statement](SECURITY.md).

## 8. Your choices and rights

You can ask to see, correct or delete personal information we hold about you, including your sign-up email address, by emailing [tom@capinora.com](mailto:tom@capinora.com). We'll respond within a reasonable time and explain any exceptions that apply.

If you have a privacy concern, contact us first. If you're not satisfied with our response, you may be able to complain to the Office of the Australian Information Commissioner at [oaic.gov.au](https://www.oaic.gov.au).

## 9. Age

ToknShield is intended for people aged 18 and over.

## 10. Changes

We'll update this policy when our practices change, and publish the new version with its effective date. Where a change is significant, we'll give extra notice, for example by email to beta testers.
