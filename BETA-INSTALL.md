# Installing the ToknShield beta

ToknShield beta 0.23.22: the Mac app plus the Chrome extension (version 0.29.14.50). Setup takes about five minutes.

You'll need a Mac with Google Chrome, an administrator password for the Mac, and ChatGPT set to English.
When you attach a supported file through ToknShield, the original stays on your Mac and ChatGPT receives only the protected copy. For this beta, use made-up or non-sensitive files, and don't select private files from Drive or ChatGPT Library.

Questions or problems: **[tom@capinora.com](mailto:tom@capinora.com)**

## 1. Download

From the [release page](https://github.com/ToknShield/ToknShield-beta/releases/tag/v0.23.22-beta), download both files:

- `ToknShield-0.23.22-beta.pkg`: the Mac app
- `ToknShield-Chrome-Extension-0.29.14.50.zip`: the Chrome extension

Double-click the zip to unzip it. Move the **ToknShield Chrome Extension** folder somewhere permanent, such as your Documents folder.
Chrome runs the extension from this folder, so if you delete or move it later, the extension stops working.

## 2. Install the Mac app

1. Quit Chrome completely: press ⌘Q while Chrome is in front. Closing the window isn't enough.
2. Open `ToknShield-0.23.22-beta.pkg` and follow the installer. macOS asks for your administrator password.
   The app is signed by Portfolioapp Pty Ltd and checked by Apple, so it opens without a security warning.
3. Open **ToknShield** from your Applications folder. A shield icon appears in the menu bar at the top of your screen.

## 3. Add the Chrome extension

1. Open Chrome and go to `chrome://extensions`. Type it into the address bar.
2. Turn on **Developer mode** (top right).
3. Click **Load unpacked**, then choose the **ToknShield Chrome Extension** folder from step 1.
4. ToknShield appears in the list. Click the puzzle-piece icon in Chrome's toolbar, then the pin, so the ToknShield icon stays visible.
5. Click the ToknShield icon and choose **Automatic**.

**About the Developer mode message.** Chrome sometimes shows a notice about extensions in developer mode. That's
expected during the beta, because ToknShield isn't on the Chrome Web Store yet. It's safe to dismiss.

## 4. Check it works

Open ChatGPT and start a **Temporary Chat** (top right). Then:

1. Send `What is the capital of France?` It goes through exactly as typed.
2. Send `Remind test@example.com about the invoice`. ChatGPT receives a placeholder such as `[[TS2_…]]` instead of the email address.
3. Type `@drive` and press Enter. ToknShield blocks it, because connected apps could share files ToknShield can't see.
4. Click the ToknShield icon, choose **Off**, and send the email message again. This time it goes through unchanged.
   Switch back to **Automatic** when you're done.

## What ToknShield protects

| What you do in ChatGPT | With protection on |
|---|---|
| Type a message | Names, emails, phone numbers, addresses and account details are replaced before sending |
| Attach a Word document (.docx) | A protected copy is sent. Documents containing pictures, embedded files or macros are refused, to be safe. |
| Attach a PDF (typed or scanned) | You see a protected copy with private details blacked out, check each page, then attach it |
| Google Drive, other connected apps, web search, @mentions | Blocked, because ToknShield can't check what they share |
| Drag, drop or paste a file, or use ChatGPT's own attach menu | Stopped. Attach files through the ToknShield panel instead. |
| Edit a message you've already sent | Blocked |

If ToknShield can't confirm something is protected, it blocks the send. It never sends the original instead.

**Seeing the original details again.** When ChatGPT replies, open ToknShield's panel and choose **Settings › Restore on this Mac**.
The original details are shown in ToknShield's own window, on your Mac only.

## If something isn't working

| What you see | What to do |
|---|---|
| "Protection paused · Chrome has updated" | Quit Chrome completely (⌘Q) and reopen it. |
| "Reconnecting to local protection…" for more than a minute | Check the ToknShield shield is in your menu bar. If not, open ToknShield from Applications. Then quit and reopen Chrome. |
| A PDF says "Ready for your review" | Use **Next page** to look at every page (the Confirm button only works after that), press **Confirm protected copy**, then **Attach**. |
| An attached file disappears from the panel | ChatGPT probably refused the upload, often because a free plan's daily file limit was reached. Nothing was sent. Check ChatGPT's own message above the message box. |
| A message is blocked | The panel says why. Remove what it mentions (for example an @mention or an app) and send again. |
| You used an earlier test version of ToknShield | Email us before installing, so we can help you remove it first. |

## Good to know

- **ChatGPT in English.** Some checks rely on ChatGPT's English button labels.
- **Web search** can't be used while protection is on. Switch to Off for that message.
- **Google Drive and ChatGPT's file library:** if you pick a file from these, ChatGPT fetches it on its own servers.
  ToknShield stops the message being sent, but it can't stop that fetch, so avoid picking private files from there.
- **In a small Chrome window,** scroll inside the ToknShield panel to find the PDF review and the Attach button.

## Updating the extension

If you installed an earlier beta extension, you don't need to reinstall the Mac app.

1. Download `ToknShield-Chrome-Extension-0.29.14.50.zip` from the release page and unzip it.
2. Replace your existing **ToknShield Chrome Extension** folder with the new one, in the same place.
3. In Chrome, go to `chrome://extensions` and click the reload arrow on ToknShield. It should now say version 0.29.14.50.

The Mac app's menu may still show "Extension 0.29.14.49". That label is fixed in the installer, and the two work together.

## Removing ToknShield

1. Quit Chrome, then quit ToknShield from the shield in the menu bar.
2. In Chrome, go to `chrome://extensions` and click **Remove** on ToknShield.
3. Open Terminal (Applications › Utilities) and paste these three lines. It asks for your Mac password.
   ```
   sudo rm -rf /Applications/ToknShield.app
   sudo rm -f /Library/Google/Chrome/NativeMessagingHosts/io.toaknshield.{status,handoff,authority,visual}.json
   sudo pkgutil --forget io.toaknshield.privatebeta
   ```
   (`io.toaknshield` is ToknShield's internal name on your Mac. The spelling is intentional.)

Removing ToknShield doesn't change ChatGPT or your documents. Protected copies you saved stay where you saved them.

**Going back to an earlier beta.** Remove this version using the steps above, then install the earlier package.
If you install an older version over a newer one, macOS reports success but keeps the newer version.

## Checking the downloads (optional)

To confirm the files are exactly what we published, run this in Terminal and compare the results with `SHA256SUMS` on the release page:

```
shasum -a 256 ~/Downloads/ToknShield-0.23.22-beta.pkg ~/Downloads/ToknShield-Chrome-Extension-0.29.14.50.zip
```
