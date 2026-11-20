# ToknShield Security and Data Handling

Last reviewed: 20 November 2026 · Version 1.0 (beta)

Provided by **Portfolioapp Pty Ltd** (ACN 688 794 247, ABN 74 688 794 247). Security contact: [tom@capinora.com](mailto:tom@capinora.com).

## Our approach

ToknShield is a local-first privacy layer for ChatGPT. Before your message or file is sent, it replaces sensitive values with placeholders on your device. Where restoring is supported, it puts the real values back on your Mac.

## Data boundary

The ToknShield extension and app make no network connections to Portfolioapp. We run no servers that receive your messages, documents or detected values.

That doesn't mean nothing leaves your Mac. The protected messages and files you choose to send go to ChatGPT, and OpenAI handles them under its own terms.

When you attach a supported file through ToknShield, the original stays on your Mac and ChatGPT receives only the protected copy.

## What's supported in this beta

**Supported:**
- typed messages in ChatGPT
- Word (.docx) files
- PDFs, including many scanned ones. Low-quality, rotated or signed scanned pages may be refused.

**Blocked while protection is on:**
- connected apps such as Google Drive
- web search and @mentions
- editing a message you've already sent
- files dragged, dropped, pasted or picked through ChatGPT's own menu

Use the ToknShield panel to attach files instead.

**Not protected:** files picked from Google Drive or ChatGPT's Library are fetched by ChatGPT itself. For this beta, use made-up or non-sensitive files, and don't select private files from Drive or ChatGPT Library.

## Controls

**Fails closed.** If ToknShield can't confirm something is protected, it blocks the send. It never falls back to the original.

**Least privilege.** The extension runs only on chatgpt.com. It asks Chrome for just these permissions:
- local storage
- the active tab
- messaging with the ToknShield app on your Mac

**Signed software.** The Mac app is signed with Portfolioapp's Apple Developer ID, and its installer is notarised by Apple. The app accepts connections only from the official ToknShield extension.

**Local storage.** Restoration data is kept on your Mac:
- in the macOS Keychain, on this device only and readable while your Mac is unlocked
- in the app's local storage

**No telemetry.** ToknShield sends no analytics, crash reports or diagnostics to us.

## Your part

- Keep the extension and the Mac app up to date.
- Check that protection is on before you send.
- Review protected previews, including every page of a PDF.
- Don't try to bypass blocks.
- Follow your organisation's rules.
- Use ChatGPT's own privacy settings.

ToknShield reduces some disclosure risks. It can't remove them all.

## Reporting a vulnerability

Please email [tom@capinora.com](mailto:tom@capinora.com) with:
- the affected versions
- clear steps to reproduce
- the impact you expect

Use synthetic test data only, and don't send real secrets or personal documents.

- **Acknowledgement:** within 5 business days.
- **Coordinated disclosure:** please give us up to 90 days to release a fix before publishing details. We'll keep you updated and agree a disclosure date with you.
- **Good faith:** if you follow this policy, avoid accessing other people's data, and don't disrupt services, we won't pursue action against you for your research.

See also the [Acceptable Use and Responsible Disclosure Policy](ACCEPTABLE-USE.md).
