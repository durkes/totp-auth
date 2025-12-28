# TOTP Generator (Local + Optional Encryption)

A lightweight, single-file web app for generating Google Authenticator style TOTP (time-based one-time password) codes. Secrets and saved entries are stored locally in your browser (Local Storage). No server, no network calls.

## Use it online

[totp-auth.pages.dev](https://totp-auth.pages.dev/)

## Features

- Generate 6-digit TOTP codes (RFC 6238 style using HMAC-SHA1)
- Save multiple entries with a friendly name
- Click any code to copy to clipboard
- Drag and drop to reorder saved entries
- Reveal a saved entry’s secret (on demand)
- Export / import as JSON for backups or moving devices
- Optional encryption:
  - Set a password to encrypt saved entries (AES-GCM + PBKDF2-SHA256)
  - Requires unlocking after reload
  - Change password (validates current password before prompting for the new one)
  - Remove encryption by setting the new password blank

## Storage

The app uses **Local Storage**:
- Plain mode: stores entries as JSON
- Encrypted mode: stores encrypted blob + encryption metadata

Nothing is synced or uploaded automatically. If you clear your browser storage, data is removed.

## Export / Import

- **Export JSON** downloads a backup file.
- **Import JSON** supports:
  - Plain exports (entries list)
  - Encrypted exports (metadata + encrypted blob)

Encrypted imports remain locked until you unlock with the correct password.

## Running the App Locally

No build tools required.

1. Save the HTML file locally (for example: `index.html`)
2. Open it in your browser

## Notes / Security

- Encryption is meant to protect saved entries on your local device.
- If you forget the password, encrypted entries cannot be recovered.
- Use export backups if you want a portable copy of your saved entries.
