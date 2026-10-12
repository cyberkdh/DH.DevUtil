# HMAC Simulator (Base)

[한국어](./HMAC_SIMULATOR.ko.md)

HMAC Simulator (Base) is a standalone, browser-based learning tool that calculates HMAC values over message bytes and exposes the construction steps for inspection.

## Features

- Calculate HMAC-SHA-256, HMAC-SHA-384, and HMAC-SHA-512.
- Enter the key and message as UTF-8 text or hexadecimal bytes.
- Inspect key normalization, `K0`, `ipad`, the inner digest, `opad`, and the final HMAC.
- View the Client → in-transit request data → Server flow in three separate panels.
- Pass only the exact message bytes (hex) and HMAC authentication tag to the editable in-transit panel. The shared secret is not included.
- Configure the Server's hash function and shared secret independently, then verify with the browser's Web Crypto API.
- Display the received message in the Server panel as a UTF-8 preview and show the exact received bytes used for verification as hex.
- Test verification failures by changing the in-transit bytes/tag, Server key, or Server hash function.
- Load RFC 4231 SHA-256 test vectors and compare the result with the expected value.
- The initial RFC 4231 test vector uses the published test key `Jefe`; both Client and Server shared-secret inputs are masked by default and have independent **Show/Hide** toggles.
- The shared secret is highlighted as a core security value: Client and Server must protect it, and it is never included in the request.
- The Server's separate shared-secret input is highlighted in the same way, with a reminder that it must match the Client's key for verification.
- Process values in the current browser without network requests, external libraries, or persistence.
- Clear the inputs and displayed intermediate values.

## How to use

1. Open [`DH.DevUtil.hmac-simulator-base.html`](../tools/DH.DevUtil.hmac-simulator-base.html) in a modern browser.
2. Select the hash function and the input encoding for the key and message.
3. Enter sample values, or select an RFC 4231 test vector.
4. On the Client, select **Create HMAC** to calculate the message authentication code. Open **Show HMAC construction steps** to inspect the intermediate values.
5. Select **Send request data**. The middle panel now contains the message's exact bytes as hex and the HMAC tag; the secret is not transferred.
6. On the Server, independently enter the shared secret and select the configured hash function. Select **Verify request**. The Server panel displays a UTF-8 preview of the received message and its exact bytes in hex.
7. Edit the in-transit message/tag or change the Server key/hash function and verify again to see a failure.
8. Use **Clear all** to clear the Client, in-transit, and Server inputs/results.

Hex input accepts whitespace between bytes but requires complete pairs of hexadecimal digits. Empty keys and messages are allowed by the calculation.
The message is represented as hex in the simulator's request panel; the Server converts it back to the exact original bytes before checking the HMAC. The Server panel shows a UTF-8 preview when the bytes are valid UTF-8; otherwise, it indicates that the bytes cannot be decoded while still displaying their exact hex representation. Client and Server hash-function settings are separate and must agree; the hash function is pre-agreed and is not sent in the basic simulated packet.
Selecting an RFC 4231 test vector loads its test key and message, then checks the calculated HMAC against the RFC's expected value. RFC 4231 identifies the complete test vector, not only its key.

## HMAC construction

For hash function `H` with block size `B`, HMAC first normalizes the key into `K0`. If the key is longer than `B`, it is hashed; otherwise, zero bytes are appended to reach `B`. The result is:

```text
H((K0 XOR opad) || H((K0 XOR ipad) || message))
```

`ipad` is the byte `0x36` repeated to the block size, and `opad` is `0x5c` repeated to the block size. SHA-256 uses a 64-byte block; SHA-384 and SHA-512 use 128-byte blocks.

The hash operations use the browser Web Crypto API. The intermediate construction is performed by the page's local JavaScript so each stage can be displayed.

## Security note

This is an educational simulator, not a production key-management tool or a substitute for a reviewed cryptographic implementation. It intentionally displays `K0`, `ipad`, and `opad`, which expose key-derived values and may reveal the effective key. **Do not enter production secrets, credentials, or sensitive messages.** The page does not save or send entered values, but other browser extensions, injected scripts, or a modified copy of the page could access them.

The middle panel is a local simulation and does not send an actual network request. The verifier represents local MAC verification only. It does not model timestamp freshness, nonce replay tracking, client authorization, network transport, or server-side secret lookup. HMAC provides message authentication and integrity, not encryption or a digital signature. The simulator does not provide password hashing, key storage, or production server-side authentication.
