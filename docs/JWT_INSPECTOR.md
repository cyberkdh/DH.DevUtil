# JWT Inspector

[한국어](./JWT_INSPECTOR.ko.md)

JWT Inspector is a local learning tool for generating and parsing the compact format of [RFC 7519](https://www.rfc-editor.org/rfc/rfc7519) JSON Web Tokens. Signature generation and verification are limited to HS256 (HMAC-SHA-256).

## Screenshot

![JWT Inspector preview](./images/DH.DevUtil.jwt-inspector.png)

The screenshot uses test values to illustrate the interface. Do not enter production JWTs or secret keys.

## Features

- Generate demo JWTs by editing a JSON protected header and claims in an emulated issuer.
- Generate a temporary 256-bit signing key with the browser's cryptographic random-number generator (CSPRNG).
- Parse the header and payload of a generated token or pasted compact JWS.
- Find registered claims (`iss`, `sub`, `aud`, `exp`, `nbf`, `iat`, `jti`) and render NumericDate time claims in UTC.
- Verify HS256 signatures and reject unsupported or mismatched `alg` values.
- Inspect parse details including segments, decoded header/payload, byte lengths, and the fact that parsing does not verify signatures.
- Inspect verification details including the signing input, key byte length, expected/received signatures, and comparison result (the key itself is never displayed).
- Require canonical Base64URL encoding for every compact segment.
- Process everything in the browser without network requests or persistent storage.

## How to use

1. Open [JWT Inspector](../tools/DH.DevUtil.jwt-inspector.html) in a modern browser.
2. In **Generate · Issuer emulation**, select **Generate temporary key**. Edit the JSON header and claims if needed.
3. The header `alg` must be `HS256`; unsupported critical extensions and `b64=false` unencoded payloads are rejected. Select **Generate JWT** to create an HS256 compact JWS in the Parser input. The Verify panel is also populated with the matching temporary key.
4. To inspect an existing token, paste it into the Parser input and select **Parse token**. Expand **Show parsing details** to inspect the three segments and decoding steps. Reading its structure does not validate its signature.
5. To verify an HS256 token, enter its key in **HS256 verification key** and select **Verify HS256 signature**. Expand **Show HS256 verification details** to inspect the HMAC input, expected/received signatures, and comparison result. The key itself is never shown in the details.

Generating a new temporary key clears the previous token and its parse/verification results to avoid confusing a token signed with an old key. Editing the key, header, or claims does not change an already generated token; generate again to apply those inputs.

## JWT format and verification semantics

A typical signed compact JWT (JWS) has three dot-separated parts:

```text
BASE64URL(protected header).BASE64URL(payload).BASE64URL(signature)
```

The header and payload are Base64URL-encoded, not encrypted. Anyone can decode them, so do not put secrets in claims. Parsing displays the token's claims; it does not establish trust.

Each segment must use canonical Base64URL encoding, including zeroed unused padding bits. Non-canonical spellings that decode to the same bytes are rejected.

A successful signature check means only that the signature matches the supplied HS256 key. The tool does not validate issuer (`iss`), audience (`aud`), expiration (`exp`), policy, or user authorization, and does not establish trust in an issuer. It never selects a verification algorithm based on the token's `alg`; algorithms other than HS256 and `alg=none` signatures are not verified. Critical header extensions and `b64=false` unencoded payloads are also rejected.

## Scope and security

This tool supports JWS compact parsing and local HS256 generation/verification only. It does not support JWE encryption/decryption, RSA/ECDSA signatures, Identity Provider integration, or policy-based claims validation. Five-part JWE compact tokens are detected and reported as unsupported.

**Do not enter production JWTs, claims containing personal data, or production signing keys.** Tokens and keys are processed in the current browser and are not saved or transmitted. Generated tokens and temporary keys are for demonstration only and must not be used for real authentication.
