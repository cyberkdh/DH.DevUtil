# TOTP / HOTP Simulator

[한국어](./TOTP_HOTP_SIMULATOR.ko.md)

Generate one-time passwords locally with the browser Web Crypto API.

## Features

- TOTP and HOTP modes.
- SHA-1, SHA-256, and SHA-512.
- Six- or eight-digit output.
- Configurable TOTP period, Unix time, and HOTP counter.
- Base32 secret decoding and displayed counter/dynamic-truncation details.

## How to use

1. Open [TOTP / HOTP Simulator](../tools/DH.DevUtil.totp-hotp.html).
2. Select the mode, hash, digits, and secret.
3. Review the generated code and change the time or counter to explore rollover behavior.

All values stay in the current browser tab. This is an educational simulator; do not enter production secrets.
