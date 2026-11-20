# ToknShield supervised beta: install, rollback and recovery

Native app 0.23.22 (build 40) with Chrome extension 0.29.14.49. For supervised testers on macOS with Google Chrome,
using synthetic documents unless the supervisor says otherwise.

## What it protects

| Workflow | Status |
|---|---|
| Typed text in ChatGPT | Protected: private details are replaced before sending |
| Local Word (.docx) files | Protected in place; files with pictures, embedded files or macros are refused |
| Local PDFs, digital or scanned | Protected copy with private areas blacked out; you review each page first |
| Google Docs downloaded as DOCX or PDF | Protected as local files |
| Google Drive, other connected apps, web search, @mentions | Blocked while protection is on |
| Editing a message you already sent | Blocked while protection is on |
| Files dropped or pasted anywhere on the page, or picked from ChatGPT's own menu | Stopped before upload while protection is on; choose the file in the ToknShield panel instead |
| Files from ChatGPT's Library | Blocked at Send while protection is on (they are already stored with ChatGPT) |
| What ChatGPT fetches by itself from a connected account | Not visible to ToknShield, so not protected |

If ToknShield cannot confirm protection, it blocks the message. It never sends the original instead.

## Download and check

Download both files from the release page:

- `ToknShield-0.23.22-beta.pkg`
- `ToknShield-Chrome-Extension-0.29.14.49.zip`

Optionally, check them in Terminal against `SHA256SUMS` on the release page:

```
shasum -a 256 ~/Downloads/ToknShield-0.23.22-beta.pkg ~/Downloads/ToknShield-Chrome-Extension-0.29.14.49.zip
```

Unzip the extension, and move the `ToknShield Chrome Extension` folder somewhere permanent, for example your
Documents folder. Chrome loads the extension from that folder, so deleting or moving it later removes the extension.

## Install

1. Quit Chrome completely (⌘Q).
2. Open `ToknShield-0.23.22-beta.pkg` and follow the installer. It needs an administrator password. It adds
   `/Applications/ToknShield.app` and four small files in `/Library/Google/Chrome/NativeMessagingHosts`
   (`io.toaknshield.status`, `.handoff`, `.authority`, `.visual`).
3. Open ToknShield from Applications. A shield appears in the menu bar.
4. Open Chrome, go to `chrome://extensions`, turn on **Developer mode**, click **Load unpacked** and choose the
   `ToknShield Chrome Extension` folder you unzipped. Check it says version 0.29.14.49 and ID
   `ecmhofklgmppejaapkngpofnaodlbifh`. Remove any other ToknShield extension so only one is enabled.
5. Click the ToknShield toolbar icon and choose **Automatic**.

## Check it works

In a ChatGPT Temporary Chat:

1. Send `What is the capital of France?` It should send unchanged.
2. Send `Remind test@example.com about the invoice`. ChatGPT should receive a `[[TS2_…]]` reference, not the address.
3. Type `@drive` and press Enter. ToknShield should block it.
4. Set the toolbar icon to **Off** and send the same address. It should go through unchanged.

## When protection stops

| What you see | What to do |
|---|---|
| "Protection paused · Chrome has updated" | Quit Chrome completely with ⌘Q (closing the window is not enough) and reopen it. |
| "Reconnecting to local protection…" for more than a minute | Make sure ToknShield is running in the menu bar. If Chrome updated recently, quit and reopen Chrome. |
| A PDF says "Ready for your review" | Use **Next page** to view every page (Confirm does nothing until you have), press **Confirm protected copy**, then **Attach**. |
| A message is blocked | The panel says why. Remove what it names (an @mention, app chip, tool, or unprotected file) and send again. |

## Roll back or remove

1. Quit Chrome and quit ToknShield from the menu bar.
2. At `chrome://extensions`, remove ToknShield, or load the previous extension folder you were given.
3. Remove the app and its Chrome registrations (administrator password needed):
   ```
   sudo rm -rf /Applications/ToknShield.app
   sudo rm -f /Library/Google/Chrome/NativeMessagingHosts/io.toaknshield.{status,handoff,authority,visual}.json
   sudo pkgutil --forget io.toaknshield.privatebeta
   ```
4. To go back to an earlier beta, do step 3 first, then install the earlier signed package. Installing an older
   package over a newer one reports success but keeps the newer app, so removing it first is required.

Removing ToknShield does not change ChatGPT or your documents. Protected copies you downloaded stay where you saved them.

## Known limits

- The installer is Developer ID signed and notarized by Apple, with the ticket stapled, so macOS opens it without a warning.
- Connected-app and Library detection relies on ChatGPT's English interface labels. Use ChatGPT in English.
- If ChatGPT refuses an upload (for example when your plan's file-attachment limit is reached), ToknShield's panel clears
  the protected file without saying why. Nothing is sent. Check ChatGPT's own message above the message box.
- A file picked from Google Drive or the Library is fetched by ChatGPT on its own servers when you pick it.
  ToknShield stops the message from being sent, but cannot stop that fetch.
- In a short Chrome window, the PDF review and the Attach button are inside the panel's scroll area.
- Web search cannot be used while protection is on; switch to Off for that message.
- Per-user Chrome registrations in `~/Library/Application Support/Google/Chrome/NativeMessagingHosts` take priority
  over the ones this installer adds. A tester who used a development build should remove those first.
