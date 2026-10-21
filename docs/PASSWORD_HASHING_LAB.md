# Password Hashing Lab

[한국어](./PASSWORD_HASHING_LAB.ko.md)

Password Hashing Lab is a browser-local learning tool for password-derived values. It demonstrates PBKDF2 with SHA-256, SHA-384, or SHA-512, configurable iterations, salt, key length, and password verification.

## Features

- Generate a random salt with the browser Web Crypto API.
- Derive PBKDF2 values with SHA-256, SHA-384, or SHA-512.
- Change iterations and derived key length to observe the parameters.
- Verify a second password against the current derived package.
- Toggle password visibility independently for the Password and Verify fields.
- Copy a storage-style JSON package containing algorithm, iterations, length, salt, and derived value.
- Switch between English and Korean UI.

## Important security notes

- This is an educational tool. Do not enter production passwords, credentials, or secrets.
- A password-derived value is not encryption and cannot be reversed into the original password.
- Salt is normally stored with the derived value; it is not a password secret, but it should be unique.
- PBKDF2 is shown because it is available through the browser Web Crypto API. Production systems should follow current platform guidance and select an appropriate password KDF for their environment.
- The tool does not claim that its default parameters are suitable for every production system.

## Privacy

All derivation and verification happen in the current browser tab. No value is uploaded or stored by the tool.
