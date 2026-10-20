# DH.DevUtil

DH.DevUtil is a collection of lightweight utilities for everyday development tasks. Each tool is a standalone HTML file that runs in a modern browser without installation or external libraries. DH.MarkDown.Flow also runs from a single standalone file (`index_local.html`), but it bundles third-party libraries such as Mermaid and docx.

[한국어](./README.ko.md)

## Tools

| Tool | What it does | Live demo | Source | Guide |
|---|---|---|---|---|
| JSON Parser | Validate, explore, format, and minify JSON. Inspect Base64 values and preview embedded images. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.json.html) | [View source](./tools/DH.DevUtil.json.html) | [Guide](./docs/JSON_PARSER.md) |
| File Hash Calculator | Calculate cryptographic hashes, checksums, and non-cryptographic hashes for local files. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.hash.html) | [View source](./tools/DH.DevUtil.hash.html) | [Algorithms and guide](./docs/HASH_ALGORITHMS.md) |
| HMAC Simulator (Base) | Calculate and verify HMAC tags and explore the Client → in-transit data → Server flow. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.hmac-simulator-base.html) | [View source](./tools/DH.DevUtil.hmac-simulator-base.html) | [Guide](./docs/HMAC_SIMULATOR.md) |
| HTTP Digest Authentication Simulator | Simulate RFC 7616 challenges, Digest responses, and server verification. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.http-digest-auth-simulator.html) | [View source](./tools/DH.DevUtil.http-digest-auth-simulator.html) | [Guide](./docs/HTTP_DIGEST_AUTH_SIMULATOR.md) |
| JWT Inspector | Generate demo JWTs with HS256, parse compact JWTs, and verify HS256 signatures. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.jwt-inspector.html) | [View source](./tools/DH.DevUtil.jwt-inspector.html) | [Guide](./docs/JWT_INSPECTOR.md) |
| Number Notation Converter | Turn E notation such as `1.23457E+15` into exact plain, grouped, engineering, SI, and Korean-unit forms, and see what a double or float32 stores. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.number-notation.html) | [View source](./tools/DH.DevUtil.number-notation.html) | [Guide](./docs/NUMBER_NOTATION_CONVERTER.md) |
| Regex Tester | Test JavaScript regular expressions, inspect matches and capture groups, preview replacements, and learn common regex syntax. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.regex-tester.html) | [View source](./tools/DH.DevUtil.regex-tester.html) | [Guide](./docs/REGEX_TESTER.md) |
| Timestamp Converter | Convert ISO, Unix, FILETIME, and .NET Ticks values, and add or subtract calendar durations. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.timestamp-converter.html) | [View source](./tools/DH.DevUtil.timestamp-converter.html) | [Guide](./docs/TIMESTAMP_CONVERTER.md) |
| Color Converter | Convert HEX, RGB, HSL, HSV, and OKLCH colors, preview combinations, and check WCAG contrast. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.color-converter.html) | [View source](./tools/DH.DevUtil.color-converter.html) | [Guide](./docs/COLOR_CONVERTER.md) |
| Text · JSON Diff | Compare plain text or formatted JSON locally and inspect additions and removals line by line. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.text-json-diff.html) | [View source](./tools/DH.DevUtil.text-json-diff.html) | [Guide](./docs/TEXT_JSON_DIFF.md) |
| CIDR Calculator | Calculate IPv4 network ranges, masks, host counts, binary values, and subnet splits. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.cidr-calculator.html) | [View source](./tools/DH.DevUtil.cidr-calculator.html) | [Guide](./docs/CIDR_CALCULATOR.md) |
| Symmetric Encryption Simulator (Base) | Learn symmetric encryption with AES, ARIA, 3DES, and DES in ECB/CBC mode, selectable padding, one shared key and IV, and a fixed IV for reproducible ciphertext. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.symmetric-encryption-simulator-base.html) | [View source](./tools/DH.DevUtil.symmetric-encryption-simulator-base.html) | [Guide](./docs/SYMMETRIC_ENCRYPTION_SIMULATOR_BASE.md) |
| Symmetric Encryption Simulator | Encrypt/decrypt with AES-GCM/CBC/CTR and compare CBC padding schemes. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.symmetric-encryption-simulator.html) | [View source](./tools/DH.DevUtil.symmetric-encryption-simulator.html) | [Guide](./docs/SYMMETRIC_ENCRYPTION_SIMULATOR.md) |
| Unicode · Encoding Inspector | Inspect code points, UTF-8/UTF-16/CP949 bytes, NFC/NFD normalization, hidden characters such as zero-width spaces and bidi controls, and mojibake; decode hex or Base64 bytes. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.unicode-inspector.html) | [View source](./tools/DH.DevUtil.unicode-inspector.html) | [Guide](./docs/UNICODE_ENCODING_INSPECTOR.md) |
| DH.MarkDown.Flow | Local-first Markdown editor with Source, WYSIWYG, and Split modes, Mermaid diagrams, and Markdown/HTML/PDF/Word export. | [Run (Ctrl-click for a new tab)](https://cyberkdh.github.io/DH.DevUtil/tools/DH.MarkDown.Flow/index.html)<br>[Download offline version (right-click → Save link as)](https://raw.githubusercontent.com/cyberkdh/DH.DevUtil/main/tools/DH.MarkDown.Flow/index_local.html) | [View files](./tools/DH.MarkDown.Flow/) | [Guide](./docs/MARKDOWN_FLOW.md) |

Live demos run the static HTML tools on GitHub Pages. The source links open the HTML files in GitHub's code viewer; they do not run the tools. To use a tool offline, clone the repository or download its HTML file, then open it in a browser. For DH.MarkDown.Flow, open `index_local.html`; `index.html` needs a web server.

## HTTP Digest Authentication Simulator preview

Explore the RFC 7616 challenge, Client response calculation, Server verification, and calculation details in one screen. See the [HTTP Digest Authentication Simulator guide](./docs/HTTP_DIGEST_AUTH_SIMULATOR.md) for features and usage.

![HTTP Digest Authentication Simulator preview](./docs/images/DH.DevUtil.http-digest-auth-simulator.png)

## JWT Inspector preview

Generate demo JWTs, parse compact tokens, and inspect HS256 signature verification details. See the [JWT Inspector guide](./docs/JWT_INSPECTOR.md) for features and usage.

![JWT Inspector preview](./docs/images/DH.DevUtil.jwt-inspector.png)

## Number Notation Converter preview

Turn E notation such as `1.23457E+15` into readable numbers with exact decimal conversion, and see what a double or float32 actually stores. See the [Number Notation Converter guide](./docs/NUMBER_NOTATION_CONVERTER.md) for features and usage.

![Number Notation Converter preview](./docs/images/DH.DevUtil.number-notation.png)

## Regex Tester preview

Test JavaScript regular expressions, inspect every match and capture group, preview replacement tokens, and learn why regex flavors differ between programming languages. See the [Regex Tester guide](./docs/REGEX_TESTER.md) for features and usage.

![Regex Tester preview](./docs/images/DH.DevUtil.regex-tester.png)

[Open the beginner-friendly Regex Guide](./tools/DH.DevUtil.regex-tester.html#guide-lessons) inside the Regex Tester with step-by-step lessons and runnable examples.

## Timestamp Converter preview

Convert timestamps between ISO 8601, Unix units, Windows FILETIME, and .NET Ticks, then calculate a new date by adding or subtracting a calendar duration. See the [Timestamp Converter guide](./docs/TIMESTAMP_CONVERTER.md) for features and usage.

![Timestamp Converter preview](./docs/images/DH.DevUtil.timestamp-converter.png)

## Color Converter preview

Convert HEX colors to RGB, HSL, HSV, and OKLCH, preview foreground/background combinations, and check WCAG contrast. See the [Color Converter guide](./docs/COLOR_CONVERTER.md) for features and usage.

![Color Converter preview](./docs/images/DH.DevUtil.color-converter.png)

## Text · JSON Diff preview

Compare plain text or formatted JSON locally and inspect added and removed lines. See the [Text · JSON Diff guide](./docs/TEXT_JSON_DIFF.md) for features and usage.

![Text · JSON Diff preview](./docs/images/DH.DevUtil.text-json-diff.png)

## CIDR Calculator preview

Calculate IPv4 network ranges, masks, host counts, binary values, and split subnets locally. See the [CIDR Calculator guide](./docs/CIDR_CALCULATOR.md) for features and usage.

![CIDR Calculator preview](./docs/images/DH.DevUtil.cidr-calculator.png)

## Symmetric Encryption Simulator (Base) preview

Encrypt and Decrypt with one shared key and IV in the middle, then compare ECB and CBC block by block. See the [Symmetric Encryption Simulator (Base) guide](./docs/SYMMETRIC_ENCRYPTION_SIMULATOR_BASE.md) for features and usage.

![Symmetric Encryption Simulator (Base) preview](./docs/images/DH.DevUtil.symmetric-encryption-simulator-base_encdec.png)

## Symmetric Encryption Simulator preview

Encrypt with AES-GCM, AES-CBC, or AES-CTR, export a JSON package without the key, and decrypt it with operation details. See the [Symmetric Encryption Simulator guide](./docs/SYMMETRIC_ENCRYPTION_SIMULATOR.md) for features and usage.

![Symmetric Encryption Simulator preview](./docs/images/DH.DevUtil.symmetric-encryption-simulator.png)

## Unicode · Encoding Inspector preview

See every code point with its UTF-8, UTF-16, and CP949 bytes, find hidden characters and NFC/NFD differences, and preview mojibake. See the [Unicode · Encoding Inspector guide](./docs/UNICODE_ENCODING_INSPECTOR.md) for features and usage.

![Unicode · Encoding Inspector preview](./docs/images/DH.DevUtil.unicode-inspector.png)

## DH.MarkDown.Flow preview

Edit Markdown in Source, WYSIWYG, or Split mode, preview Mermaid diagrams, and export to Markdown, HTML, PDF, or Word. See the [DH.MarkDown.Flow guide](./docs/MARKDOWN_FLOW.md) for features and usage.

![DH.MarkDown.Flow preview](./docs/images/DH.MarkDown.Flow.png)

## Important

- Tools process input in the current browser and do not upload it to a DH.DevUtil server.
- Do not enter production secrets or credentials in HMAC Simulator (Base). It intentionally displays key-derived intermediate values.
- Do not enter production passwords or credentials in HTTP Digest Authentication Simulator. Digest responses and calculation steps contain password-derived values.
- Do not enter production JWTs, personally identifiable claims, or production signing keys in JWT Inspector.
- Do not enter production keys or personal data in Symmetric Encryption Simulator (Base). It displays keys and intermediate values, uses a fixed IV by default, and includes DES/3DES for learning only.
- Do not enter production keys or personal data in Symmetric Encryption Simulator. AES-CBC and AES-CTR do not authenticate ciphertext.
- Legacy hashes and non-cryptographic checksums are not suitable for security against malicious changes. See the [hash security notes](./docs/HASH_ALGORITHMS.md).
- DH.MarkDown.Flow stores drafts in the browser's local storage and loads external images referenced by a document from the network. It bundles third-party libraries listed in its [third-party notices](./tools/DH.MarkDown.Flow/THIRD_PARTY_NOTICES.md).
- When using a downloaded copy or embedding a tool in another page, verify and trust its source and the surrounding browser environment.

## Getting Started

1. Select **Run** in the tool catalog to use a live demo, or clone this repository/download the HTML file for offline use.
2. Follow the corresponding tool guide.

## Recent Changes

See the [changelog](./CHANGELOG.md) for unreleased updates and release history.

## Project

- [Contributing](./CONTRIBUTING.md)
- [Security policy](./SECURITY.md)
- [MIT License](./LICENSE)
