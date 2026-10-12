# Changelog

[한국어](./CHANGELOG.ko.md)

Notable changes to DH.DevUtil are listed here. The newest changes appear first.

## [Unreleased]

### Added

- HMAC Simulator (Base), a browser-based learning tool for HMAC-SHA-256/384/512 with construction details and a Client → in-transit data → Server verification flow.
- HMAC Simulator (Base) screenshot in the English and Korean tool guides.

### Improved

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
