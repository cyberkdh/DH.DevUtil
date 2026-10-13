# Symmetric Encryption Simulator

[한국어](./SYMMETRIC_ENCRYPTION_SIMULATOR.ko.md)

The Symmetric Encryption Simulator demonstrates symmetric encryption and decryption locally in the browser. It supports AES-GCM, AES-CBC, AES-CTR, and selectable AES-CBC padding schemes.

To learn the basics first (the same key and IV on both sides, ECB vs. CBC, padding, with ARIA/3DES/DES and a fixed IV), see [Symmetric Encryption Simulator (Base)](./SYMMETRIC_ENCRYPTION_SIMULATOR_BASE.md).

## Screenshot

![Symmetric Encryption Simulator preview](./images/DH.DevUtil.symmetric-encryption-simulator.png)

The screenshot uses synthetic text and a temporary key to illustrate the interface. Do not enter production keys or personal data.

## Features

- Generate random 128-, 192-, or 256-bit AES keys. In the tested browser, AES-GCM/CTR use 128/256-bit keys and AES-CBC also supports 192-bit keys.
- AES-GCM authenticated encryption (AEAD), with a fresh 96-bit nonce, optional Additional Authenticated Data (AAD), and tamper detection.
- AES-CBC padding choices: PKCS#7, ANSI X.923, Zero, and NoPadding.
- AES-CTR with a 128-bit initial counter block and a 64-bit counter field.
- Export/import a JSON package containing algorithm parameters and ciphertext, never the secret key.
- Decrypt a package with its matching key and inspect operation details.
- Explain why DES/3DES are legacy ciphers and why ARIA is not implemented here.
- Process and generate keys in the browser without network requests or persistent storage.

## How to use

1. Clone the repository or download the HTML together with `tools/vendor/noble-ciphers-2.4.0`, then open [Symmetric Encryption Simulator](../tools/DH.DevUtil.symmetric-encryption-simulator.html) in a modern browser. The local folder is required for AES-CBC padding options.
2. Select an AES mode and key size, then select **Generate key**. Enter synthetic test text if needed.
3. For AES-CBC, select a padding scheme. **No padding** requires the UTF-8 byte length to be a multiple of 16. AES-GCM and AES-CTR do not use block padding.
4. Select **Encrypt**. Copy the generated JSON package if you want to keep it. Decryption requires the matching AES key.
5. Paste or edit a package and select **Decrypt package**.

## Modes and padding

### AES-GCM

Galois/Counter Mode (GCM) is an AEAD mode that combines encryption and authentication. The tool generates a fresh 12-byte nonce for each operation. Reusing a nonce with the same key can cause severe security failures; production systems need a deliberate nonce strategy. AAD is authenticated with the ciphertext but remains visible.

### AES-CBC

Cipher Block Chaining (CBC) uses block padding for arbitrary-length plaintext. This tool offers:

- **PKCS#7**: fills each padding byte with the number of padding bytes. It adds a full 16-byte block when input is already block-aligned.
- **ANSI X.923**: records the padding length in the last byte and fills preceding padding bytes with zero. It also adds a padding block to block-aligned input.
- **Zero padding**: fills the remainder with zero bytes. Since original trailing zero bytes are ambiguous, the package stores `plaintextLength`; this metadata is not authenticated.
- **NoPadding**: only accepts input whose UTF-8 byte length is a multiple of 16.

CBC does not provide ciphertext integrity or sender authentication. A padding check or successful decryption does not prove that data is genuine or unchanged. Prefer an AEAD mode such as GCM for production designs.

### AES-CTR

Counter (CTR) mode handles arbitrary-length input and does not use block padding. The tool creates a random 128-bit initial counter block and uses a 64-bit counter field. Never reuse a counter block with the same key. CTR alone does not detect tampering.

## Implementation and supported scope

- AES-GCM and AES-CTR use the browser Web Crypto API.
- AES-192 support in Web Crypto AES-GCM/CTR varies by browser. The tested browser rejects it, so the selector restricts 192-bit keys to AES-CBC; the local library supports AES-CBC with all three key sizes.
- AES-CBC uses a local copy of `@noble/ciphers` 2.4.0 under the MIT license to provide selectable padding. The library is stored in `tools/vendor/noble-ciphers-2.4.0`; the page does not load it from a CDN or request it over the network. See that vendor folder for licensing and upstream details.
- Imported/exported data uses a learning-only version 1 JSON package containing mode parameters, padding where applicable, and ciphertext. It is not a standardized cryptographic container format.
- ARIA is not implemented in this browser/Web Crypto-based version. DES and 3DES/TDEA are legacy ciphers and are not offered as runnable encryption options.
- ECB is omitted because it reveals repeated plaintext patterns.

## Security

**Do not enter production keys, personal information, or sensitive plaintext.** AES-CBC and AES-CTR do not authenticate data. The Zero-padding length metadata and CBC/CTR packages are also unauthenticated. This is a teaching tool, not a secure-storage solution or a replacement for production encryption.
