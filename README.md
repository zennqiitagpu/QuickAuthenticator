# QuickAuthenticator

A lightweight two-factor authentication (2FA) app for Android.  
Generates TOTP and HOTP one-time passwords fully on-device — no internet connection required.  
Supports an **overlay** on top of other apps so you can view and copy codes without leaving the screen you are on (e.g. a login page).

<img width="256" height="256" alt="ic_launcher 512x512" src="https://github.com/user-attachments/assets/5c50f7b9-5b81-4c3b-a314-00b69cc28922" />

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](buymeacoffee.com/zennqiitagp)

<img width="" height="512" alt="image" src="https://github.com/user-attachments/assets/1975a4ce-de06-4933-b314-c486c9535cc3" />
<img width="" height="512" alt="image" src="https://github.com/user-attachments/assets/7272ad76-2a55-4b76-bc19-6c1c22d4c609" />

---

## Features

- **QR code scanning** — Add accounts by scanning a standard `otpauth://` QR code from any service's 2FA setup page.
- **Manual entry** — Enter a setup key directly if a QR code is not available.
- **TOTP & HOTP support** — Compatible with RFC 6238 / RFC 4226 accounts (Google, GitHub, Dropbox, and many more).
- **Multiple algorithms** — SHA-1, SHA-256, and SHA-512.
- **6 and 8 digit codes** — Both lengths used by popular services.
- **Circular countdown timer** — Time remaining before a code expires, with a ring that shifts from green to orange to red.
- **One-tap copy** — Tap any account row to copy its current code to the clipboard.
- **Long-press actions** — Rename or delete an account.
- **Biometric / device credential lock** — Unlock before opening the main app or the overlay (skipped if the device has no lock configured).
- **Persistent notification** — A low-priority foreground notification keeps the service alive and offers quick actions (not a live OTP ticker in the shade).
- **Overlay on top of other apps** — From the notification, show your OTP list as a floating panel over whatever app you are using; tap a row to copy, tap outside to dismiss. Requires the “Display over other apps” permission the first time.
- **Manual export / import** — Save or restore accounts as a `.otpdump` file to any folder on the device (for migration or a second phone). This is **separate from** Android’s automatic cloud backup, which is disabled for this app.
- **Boot persistence** — The notification service restarts after reboot; an optional accessibility helper can restore the notification if needed.
- **Encrypted storage** — Secret keys are encrypted with AES-256-GCM via Android Keystore before being written to the local database.
- **No internet permission** — Secrets never leave your device through the app itself.

---

## Requirements

- Android 8.0 (API level 26) or later

---

## Installation

Download the latest APK from the [Releases](../../releases) page and install it on your device.

> **Note:** You may need to allow installation from unknown sources in your Android settings if you are installing outside of the Play Store.  
> Go to **Settings → Apps → Special app access → Install unknown apps** and enable it for your browser or file manager.

---

## How to Use

### Adding an account

1. Open QuickAuthenticator and complete biometric or screen-lock unlock if prompted.
2. Grant **notification permission** when asked (required for the foreground service).
3. Tap **Add OTP** (floating action button).
4. Choose **Scan QR code** or **Enter setup key**.
5. The account appears in the list and codes update automatically.

### Copying a code

- **In the app or overlay** — Tap the account row.

### Notification actions

Expand or open the QuickAuthenticator notification:

- **Open in app** — Unlock and open the main list.
- **Open in overlay** — Unlock and show the floating OTP panel over other apps.

### Deleting or renaming

Long-press an account in the main list, then choose rename or delete.

> **Warning:** Deleting an account removes it from QuickAuthenticator. Disable 2FA on the service or keep another recovery method first.

### Export / import (`.otpdump`)

1. In the main screen toolbar menu (**⋮**), choose **Export OTP backup** or **Import OTP backup**.
2. **Export** — Pick a save location; a timestamped `.otpdump` file is written.
3. **Import** — Pick an existing file; new accounts are added and matching secrets are updated.

> **Security note:** A `.otpdump` file contains **decrypted secret keys** (Base32). Store it only where you trust, and do not treat it like an encrypted Android backup. System cloud backup is turned off (`allowBackup="false"`), but exported files are entirely under your control.

---

## Security & Privacy

| Topic | Detail |
|---|---|
| Secret key storage | AES-256-GCM via Android Keystore; ciphertext only in Room |
| Network access | None — no internet permission |
| Android cloud backup | Disabled (`allowBackup="false"`) |
| Manual `.otpdump` | User-initiated; includes plaintext secrets |
| Data collection | None — no analytics or telemetry |

Your 2FA secrets are stored only on your device, encrypted with a hardware-backed key that never leaves the secure hardware.

---

## License

This software is provided free of charge. See the [LICENSE](LICENSE) file for details.
