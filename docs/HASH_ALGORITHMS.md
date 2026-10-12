# File Hash Calculator — Algorithm Guide

[File Hash Calculator](../tools/DH.DevUtil.hash.html) reads selected files in the browser and displays results from the algorithms below. Results depend on the input bytes, algorithm variant, seed, and output length.

[한국어 안내](./HASH_ALGORITHMS.ko.md)

![File Hash Calculator](./images/file-hash-calculator.png)

## Cryptographic Hashes and XOFs

| Family | Algorithm | Output | Description |
|---|---|---:|---|
| SHA-2 | SHA-224 | 224 bit | Variant with a distinct initial state in the SHA-256 family |
| SHA-2 | SHA-256 | 256 bit | Uses the Web Crypto API |
| SHA-2 | SHA-384 | 384 bit | Uses the Web Crypto API |
| SHA-2 | SHA-512 | 512 bit | Uses the Web Crypto API |
| SHA-3 | SHA3-224 | 224 bit | Keccak-based SHA-3 standard |
| SHA-3 | SHA3-256 | 256 bit | Keccak-based SHA-3 standard |
| SHA-3 | SHA3-384 | 384 bit | Keccak-based SHA-3 standard |
| SHA-3 | SHA3-512 | 512 bit | Keccak-based SHA-3 standard |
| SHAKE | SHAKE128 (256-bit output) | 256 bit | Fixed-length XOF output |
| SHAKE | SHAKE256 (512-bit output) | 512 bit | Fixed-length XOF output |

SHAKE is an extendable-output function (XOF). This tool fixes each output length for consistent file-result comparison. SHAKE digests produced with other output lengths are not directly comparable.

## Legacy Hashes

| Algorithm | Output | Intended use |
|---|---:|---|
| SHA-1 | 160 bit | Compatibility with legacy systems and file formats |
| MD4 | 128 bit | Legacy compatibility |
| MD5 | 128 bit | Legacy compatibility |

SHA-1, MD4, and MD5 are cryptographically weak and do not provide reliable collision resistance. Do not use them for new security designs, signatures, password storage, or file integrity against an attacker. The tool separates them as legacy/insecure algorithms.

## Checksums and Non-Cryptographic Hashes

| Category | Algorithm | Settings |
|---|---|---|
| CRC | CRC-8/SMBUS | width 8, polynomial `07`, init `00`, xorout `00` |
| CRC | CRC-16/CCITT-FALSE | width 16, polynomial `1021`, init `ffff`, non-reflected |
| CRC | CRC-32/ISO-HDLC | width 32, reflected polynomial `edb88320`, init/xorout `ffffffff` |
| CRC | CRC-64/ECMA-182 | width 64, polynomial `42f0e1eba9ea3693`, init/xorout `0` |
| Checksum | Adler-32 | Adler-32 checksum |
| Checksum | Fletcher-32 | Big-endian 16-bit words; append `00` after the final byte for odd-length input |
| Non-cryptographic hash | FNV-1a 32 | 32-bit |
| Non-cryptographic hash | FNV-1a 64 | 64-bit |
| Non-cryptographic hash | xxHash32 | seed `0` |
| Non-cryptographic hash | xxHash64 | seed `0` |
| Non-cryptographic hash | MurmurHash3 x86 32 | seed `0` |
| Non-cryptographic hash | CityHash64 | 64-bit variant |
| Non-cryptographic hash | FarmHash Fingerprint64 | Fingerprint64 variant |
| Non-cryptographic hash | MetroHash64 v1 | version 1, seed `0` |
| Non-cryptographic hash | Jenkins One-at-a-time | 32-bit |

Non-cryptographic checksums and hashes are intended for accidental-change detection or data-structure/identification use. They are not secure against intentional modification by an attacker. CRC variants can differ even at the same width; verify that the algorithm name and parameters match when comparing results.

## Result Representation

- Results are hexadecimal (Hex) by default. You can select lowercase, uppercase, or Base64 output per file.
- Output format changes only how digest bytes are encoded; it does not change the digest calculation.
- When comparing integer digests from different libraries, check for byte-order/endian differences.

## Out of Scope

HMAC is a message authentication code (MAC) that takes a secret key and has a different purpose and UI from ordinary file hashing. It is not included in this tool. A `realm` is not a required input to HMAC itself.
