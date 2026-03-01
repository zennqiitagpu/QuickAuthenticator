# QuickAuthenticator

A lightweight two-factor authentication (2FA) app for Android.  
Generates TOTP and HOTP one-time passwords fully on-device — no internet connection required.

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/zennqiitagpu)

---

## Features

- **QR code scanning** — Add accounts instantly by scanning a QR code from any service's 2FA setup page.
- **Manual entry** — Enter a setup key directly if a QR code is not available.
- **TOTP & HOTP support** — Compatible with standard RFC 6238 / RFC 4226 authenticator accounts (Google, GitHub, Dropbox, and many more).
- **Multiple algorithms** — Supports SHA-1, SHA-256, and SHA-512.
- **6 and 8 digit codes** — Works with both code lengths used by popular services.
- **Circular countdown timer** — Displays the time remaining before a code expires. The ring changes color from green to orange to red as the deadline approaches.
- **One-tap copy** — Tap any account in the list to copy its code to the clipboard instantly.
- **Persistent notification** — Live OTP codes shown in the notification drawer, refreshed every second, so you can read your code without unlocking the app.
- **Boot persistence** — The notification service restores automatically after a device reboot.
- **Encrypted storage** — All secret keys are encrypted with AES-256-GCM using the Android Keystore before being saved to the device. Plain-text secrets are never written to disk.
- **No backup** — App data is excluded from Android cloud backups to protect your secrets.
- **No internet permission** — The app does not use the network at all; your secrets never leave your device.

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

1. Open QuickAuthenticator.
2. Grant the **notification permission** if prompted (required for the live notification feature).
3. Tap the **+** button in the bottom-right corner.
4. Choose one of the two methods:
   - **Scan QR Code** — point your camera at the QR code shown on the service's 2FA setup page.
   - **Enter Setup Key** — type or paste the secret key provided by the service.
5. The account will appear in the list and start generating codes immediately.

### Copying a code

- **In the app** — Tap the account row to copy its current code to the clipboard.
- **In the notification** — Expand the notification and tap the **Copy** button next to any account.

### Deleting an account

Long-press the account row in the app list, then confirm deletion in the dialog.

> **Warning:** Deleting an account removes it permanently from QuickAuthenticator.  
> Make sure you have disabled 2FA on the corresponding service first, or have a backup recovery method, to avoid being locked out.

---

## Security & Privacy

| Topic | Detail |
|---|---|
| Secret key storage | AES-256-GCM, encrypted via Android Keystore |
| Network access | None — no internet permission requested |
| Cloud backup | Disabled (`allowBackup="false"`) |
| Data collection | None — no analytics, no telemetry |

Your 2FA secrets are stored only on your device, encrypted with a hardware-backed key that never leaves the secure hardware.
