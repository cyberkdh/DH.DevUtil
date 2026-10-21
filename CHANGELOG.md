# Changelog

[한국어](./CHANGELOG.ko.md)

Notable changes to DH.DevUtil are listed here. The newest changes appear first.

## [Unreleased]

### Added

- Add TOTP/HOTP Simulator, UUID/ULID Inspector, URL/Query Parser, Cron Explainer, Asymmetric Cryptography Simulator, and generic API Request Signing Simulator as standalone local HTML tools with English/Korean guides.
- Add RIPEMD-160 to File Hash Calculator as a legacy compatibility algorithm.
- Add PEM/DER certificate file picker and editor drag-and-drop loading to PEM · ASN.1 · X.509 Viewer, with stronger button hover/focus contrast.
- Add JKS certificate-chain extraction and PKCS#12/PFX outer ASN.1 inspection without displaying private-key material.

- Add CIDR Calculator for local IPv4 network, mask, host-range, binary, and subnet-split calculations with English and Korean UI.
- Add Password Hashing Lab for browser-local PBKDF2 learning with salt, iterations, key length, verification, English/Korean UI, and a guide.
- Add MIME · Content-Type Inspector for local media type parsing, parameters, suffixes, charset, extension hints, English/Korean UI, and a guide.
- Add YAML · JSON Converter for common configuration-style conversion, samples, English/Korean UI, and a guide.
- Show the selected YAML/JSON sample source before conversion.
- Add PEM · ASN.1 · X.509 Viewer for local PEM/DER parsing, ASN.1 trees, common certificate fields, English/Korean UI, and a guide.
- Add a Show passwords option to Password Hashing Lab for both password inputs.

- Add Text · JSON Diff for local line-based text comparison, JSON formatting, color-coded additions/removals, English/Korean UI, and a screenshot.
- Add multiple Text · JSON Diff samples and local file1/file2 drag-and-drop loading.
- Make the file1/file2 editor textareas themselves the drag-and-drop targets.
- Normalize UTF-8 BOM and CRLF/LF/CR line endings before Text · JSON Diff comparison.
- Add Unified, Side-by-side, Inline, and JSON Path views with whitespace/case filters, changed-only mode, and context-line selection.
- Add Word, Character, Moved lines, Summary, JSON Tree, Patch, and Change heatmap views, plus blank-line/comment/property-order/trailing-comma ignore options.
- Add a viewport-sized scroll area for Diff result and local file saving for the current Diff view.
- Hide the page scrollbar visually while preserving page scrolling, so the Diff result scrollbar is the primary visible scrollbar.
- Add Collapse/Expand control to the Comparison input panel.
- Add Color Converter for HEX, RGB, HSL, HSV, and OKLCH conversion, color previews, WCAG contrast checks, and English/Korean learning text.
- Add Timestamp Converter for ISO 8601, Unix seconds/milliseconds/microseconds/nanoseconds, Windows FILETIME, .NET Ticks, and calendar duration arithmetic, with English and Korean guides and a screenshot.
- Add Regex Tester, a browser-local JavaScript `RegExp` learning tool that displays matches, numbered and named capture groups, indexes, replacement previews, common examples, and regex flavor notes, with English and Korean guides and a screenshot.
- Add Unicode · Encoding Inspector, which shows code points, UTF-8/UTF-16/CP949 bytes, grapheme counts, NFC/NFD/NFKC/NFKD forms, hidden characters (zero-width, bidi controls, BOM, unusual spaces, lone surrogates) with line:column positions, mojibake previews, and a per-character table with Hangul decomposition. Bytes mode decodes hex or Base64 as UTF-8, CP949, UTF-16LE/BE, and Windows-1252. Adds English and Korean guides, README entries, and a screenshot.
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

- Improve YAML · JSON Converter button hover contrast and active feedback.
- Expand the Color Converter contrast preview from one sample sentence to a small interface preview with heading, paragraph, link, button, and input styles.
- Place the Color Converter WCAG controls/results beside the preview on desktop and add small, body, large, and heading text samples.
- Add buttons to apply the selected color to the WCAG foreground or background, and to swap the two contrast colors.
- Add optimized contrast color suggestions: best black/white contrast and hue-preserving AA/AAA candidates, each with an apply action for foreground or background.
- Add target contrast selection, neutral-gray recommendations, and a derived Primary/Surface/Dark/Canvas starter palette.
- Show current foreground/background in the suggested palette and display all suggested contrast colors in the right-side preview.
- Show each suggested color in a paired sample box using the actual counterpart foreground or background color.
- Add the counterpart label and HEX value inside every suggested palette swatch.
- Format Timestamp Converter local date/time using the selected UI locale, including Korean date and AM/PM formatting while preserving standard ISO output.
- Show the selected `datetime-local` value again in a localized preview below the native browser control.
- Integrate the 14-lesson Regex Guide into the Regex Tester page; the guide button now scrolls to in-page lessons and each sample loads into the current tester without opening another document.
- Present the integrated Regex Guide as an internal modal popup with close button, backdrop click, Escape-key close, and focus return.
- Expand the integrated Regex Guide to 33 samples covering URLs, UUIDs, IPv4, SemVer, colors, filenames, JSON, CSV, HTML, Markdown, environment variables, SQL parameters, dates, times, and more.
- Add a full English/Korean interface switch to Regex Tester, including localized flags, examples, statuses, match details, and a Korean screenshot.
- Add Regex flavor preview for JavaScript, Python, .NET, Java, PCRE2, and Rust, including notes for flags that are handled by matching APIs rather than compilation options.
- Add standalone Regex Guide with step-by-step lessons, practical samples, performance warnings, English/Korean UI, and Try in Tester links.
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
