# Changelog

[한국어](./CHANGELOG.ko.md)

Notable changes to DH.DevUtil are listed here. The newest changes appear first.

## [Unreleased]

### Added

- Add DH.MarkDown.Flow, a local-first Markdown editor with Source, WYSIWYG, and Split modes, Mermaid diagram preview, rendering themes, and Markdown/HTML/PDF/Word export. It ships as a web build (`index.html`) and a standalone single-file build (`index_local.html`) with its license and third-party notices, and adds English and Korean guides, README entries, and a screenshot.
- Add Number Notation Converter, which converts E notation, powers of ten, digit-separated, hex/binary/octal, and hex-float input into exact plain, grouped, scientific, engineering, SI-prefix, and Korean-unit forms, shows the exact IEEE 754 double/float32 stored values, warns about integers above 2<sup>53</sup> − 1 and Excel's 15-digit limit, and explains them in English and Korean.
- Add Symmetric Encryption Simulator (Base), a dependency-free learning tool for AES, ARIA, 3DES, and DES in ECB and CBC modes with PKCS#7, ANSI X.923, ISO/IEC 7816-4, Zero, and No padding, a shared key/IV panel used by both Encrypt and Decrypt, a fixed IV for reproducible ciphertext, step-by-step details, built-in explanations of IV and padding behavior, and NIST/RFC 5794/DES test vectors.
- Add Symmetric Encryption Simulator (Base) and Symmetric Encryption Simulator screenshots to the English and Korean READMEs and tool guides, and link the Symmetric Encryption Simulator guides to the Base guide.
- HTTP Digest Authentication Simulator, a local RFC 7616 challenge-response and verification learning tool supporting all six registered algorithm tokens with `qop=auth`.
- HTTP Digest Authentication Simulator supports the RFC 7616 `userhash=true` option.
- Add JWT Inspector to generate demo JWTs with HS256, parse compact tokens, and verify HS256 signatures locally.
- Add the JWT Inspector screenshot to the English and Korean READMEs and tool guides.
- Add a Symmetric Encryption Simulator for AES-GCM/CBC/CTR and CBC padding comparisons. AES-CBC runs on a built-in JavaScript AES implementation, so the tool needs no external libraries.
- Add the HTTP Digest Simulator screenshot to the English and Korean READMEs and tool guides.
- HMAC Simulator (Base), a browser-based learning tool for HMAC-SHA-256/384/512 with construction details and a Client → in-transit data → Server verification flow.
- HMAC Simulator (Base) screenshot in the English and Korean tool guides.

### Improved

- Add JWT Inspector parse-segment and detailed HS256 signature verification views.
- Support PKCS#7, ANSI X.923, Zero, and NoPadding options in AES-CBC.
- HTTP Digest Authentication Simulator shows Server-side calculation details for successful and failed response verification.
- README notes that Ctrl-click opens GitHub Pages live demos in a new tab because GitHub strips custom link targets.
- README distinguishes GitHub Pages live demos from source-code links.
- README explains that GitHub's code viewer does not run the HTML files.
- JSON Parser recognizes valid Base64 values without trailing padding and reports why malformed Base64 data cannot be decoded.
- JSON Parser validates embedded image data before reporting a successful preview and displays errors for corrupt or unsupported images.

## [1.0.0] - 2026-10

First public version of the repository.

### JSON Parser

- Validate JSON and display syntax errors, root type, value/member counts, nesting depth, and input size.
- Explore JSON in a collapsible tree or JSON text view; format, minify, and copy results.
- Inspect Base64 values as Base64, Hex, C# `byte[]`, or C++ `unsigned char` arrays.
- Preview and download recognized Base64 images.

### File Hash Calculator

- Select or drop multiple local files and calculate 28 algorithms:
  - SHA-2: SHA-224, SHA-256, SHA-384, SHA-512
  - SHA-3: SHA3-224, SHA3-256, SHA3-384, SHA3-512
  - SHAKE: SHAKE128 (256-bit output), SHAKE256 (512-bit output)
  - Legacy: SHA-1, MD4, MD5
  - CRC: CRC-8/SMBUS, CRC-16/CCITT-FALSE, CRC-32/ISO-HDLC, CRC-64/ECMA-182
  - Checksums: Adler-32, Fletcher-32
  - Non-cryptographic: FNV-1a 32/64, xxHash32/64, MurmurHash3 x86 32, CityHash64, FarmHash Fingerprint64, MetroHash64 v1, Jenkins One-at-a-time 32
- Choose lowercase Hex, uppercase Hex, or Base64 output per file; copy or delete individual results.
- Copy all results or save them as a UTF-8 text file.

### Repository

- Add English documentation with Korean translations, contributing and security policies, and the MIT License.
