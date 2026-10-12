# HTTP Digest Authentication Simulator

[한국어](./HTTP_DIGEST_AUTH_SIMULATOR.ko.md)

The HTTP Digest Authentication Simulator is a standalone, browser-based learning tool for the challenge-response flow in [RFC 7616](https://www.rfc-editor.org/rfc/rfc7616).

## Preview

![HTTP Digest Authentication Simulator preview](./images/DH.DevUtil.http-digest-auth-simulator.png)

## Features

- Simulate a Server challenge, Client response, and Server verification in three panels.
- Select all six RFC 7616 algorithm tokens: `MD5`, `MD5-sess`, `SHA-256`, `SHA-256-sess`, `SHA-512-256`, and `SHA-512-256-sess`.
- Calculate `qop=auth` responses, including the distinct `-sess` HA1 calculation.
- Inspect HA1, HA2, and response inputs and values.
- Inspect the Server's recalculated HA1, HA2, and expected response using the supplied account credentials, including failed comparisons.
- Display an HTTP `Authorization: Digest` header and pass an editable local JSON representation to the verifier.
- Optionally enable `userhash=true`; the Client sends `H(username:realm)` while the Server uses the separately entered account User ID to verify it.
- Load the RFC 7616 Section 3.9.1 example inputs.
- Generate a 256-bit nonce with the browser's cryptographic random-number generator.
- Use UTF-8 input and Unicode NFC normalization for the username and password.
- Run local MD5 and SHA-512/256 implementations with startup known-answer checks; SHA-256 uses the Web Crypto API.
- Process values in the current browser without network requests, external libraries, or persistence.

## How to use

1. Open [`DH.DevUtil.http-digest-auth-simulator.html`](../tools/DH.DevUtil.http-digest-auth-simulator.html) in a modern browser.
2. In **Server · Challenge**, choose an algorithm and set the realm, nonce, optional opaque value, and `qop=auth`.
3. Enter the Client username, password, method, request URI, nonce count, and client nonce.
4. Select **Calculate response**. Review the generated `Authorization` header and, optionally, the HA1/HA2 calculation steps.
5. In **Server · Verify**, enter the Server account User ID and password in that order. The User ID may be left blank when `userhash` is disabled; it is required when `userhash=true`. Verify the received data, then expand **Show Server verification calculation steps** to inspect the Server-side calculation whether verification succeeds or fails. Edit the JSON packet to explore tampering and failure cases.
6. Select **Load RFC 7616 example** to load the Section 3.9.1 MD5 values. Change the challenge algorithm to SHA-256 and calculate again to compare that RFC example too.

## Digest calculation

For `qop=auth`, the tool calculates:

```text
HA1 = H(username ":" realm ":" password)
HA1-sess = H(HA1 ":" nonce ":" cnonce)
HA2 = H(method ":" request-uri)
response = H(HA1 ":" nonce ":" nc ":" cnonce ":" qop ":" HA2)
```

The `-sess` tokens use `HA1-sess` in the response formula; the other tokens use the initial `HA1`. If `userhash=true`, the username sent in the Authorization header is additionally calculated as `H(username ":" realm)`; the original account username remains the input to HA1. Digest values are lowercase hexadecimal. `SHA-512-256` is the SHA-512/256 variant with its own initial state, not a truncated SHA-512 digest.

## Scope and security

This simulator supports only `qop=auth`. It does not implement `auth-int`, `username*`, `Authentication-Info`/`rspauth`, server-side nonce freshness or replay tracking, or a real HTTP exchange. The challenge displays UTF-8 semantics; username and password are normalized to NFC before hashing. Other internationalization and HTTP parsing behavior is outside this tool's scope.

HTTP Digest Authentication is vulnerable to offline password guessing and does not replace TLS. MD5 is retained because it is an RFC 7616 token, not because it is recommended for new security designs. **Use synthetic sample credentials only; never enter production passwords or secrets.** The page does not save or send inputs, but browser extensions, injected scripts, or a modified copy could access them. The verifier is educational and is not a production authentication server.
