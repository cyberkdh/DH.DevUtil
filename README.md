# DH.DevUtil

DH.DevUtil is a collection of lightweight utilities for everyday development tasks. Each tool is provided as a standalone HTML file that runs directly in a web browser, with no build step or package installation required.

[한국어](./README.ko.md)

## Tools

| Tool | Description |
|---|---|
| [JSON Parser](./tools/DH.DevUtil.json.html) | Validate and explore JSON as a tree or raw text. Supports formatting, minification, Base64 decoding, and image preview. See the [JSON Parser guide](./docs/JSON_PARSER.md). |
| [File Hash Calculator](./tools/DH.DevUtil.hash.html) | Calculate cryptographic hashes, checksums, and non-cryptographic hashes for local files. Supports per-file results, copy, delete, output format selection, and download. See the [algorithm guide](./docs/HASH_ALGORITHMS.md). |

## Screenshots

**JSON Parser**

![JSON Parser](./docs/images/json-parser-overview.png)

**File Hash Calculator**

![File Hash Calculator](./docs/images/file-hash-calculator.png)

## Getting Started

1. Clone the repository or download the HTML file for the tool you want to use.
2. Open the HTML file from the `tools` folder in a web browser.
3. For JSON Parser, paste JSON text and select `Parse`. For File Hash Calculator, select or drop files.

The tools include their CSS and JavaScript and do not require external JavaScript libraries or runtimes.

### JSON Parser

- Validate JSON input and display syntax errors.
- Explore objects and arrays in a collapsible **Tree** or **JSON** text view.
- Format with 2- or 4-space indentation, minify, and copy the result.
- Inspect root type, value/member counts, depth, and input size.
- View Base64 data as Hex, C# `byte[]`, or a C++ byte array. Recognized Base64 images can be previewed and downloaded.

## Privacy and Local Processing

The File Hash Calculator processes selected files in the current browser. The tools in this repository do not implement file uploads or analytics telemetry. File data is processed in browser memory during hash calculation.

When running downloaded files or using the tools in an untrusted environment, verify the source and contents of the HTML first. If you embed a tool in another web page, that page and its scripts must also be trusted.

## Hash Tool Security Notes

- SHA-1, MD4, and MD5 are provided for legacy compatibility only. Do not use them for new security designs, digital signatures, password storage, or protection against malicious tampering.
- CRC, Adler-32, Fletcher-32, and non-cryptographic hashes are intended for accidental-error detection or identification; they do not provide authentication or integrity protection against attackers.
- SHAKE128 and SHAKE256 output lengths are fixed at 256 bits and 512 bits, respectively.
- HMAC and keyed hashes that require a secret key are not included in the file hash tool.

## Supported Environment

A modern desktop browser is recommended. SHA-256/384/512 use the browser's Web Crypto API and require a browser context that provides this API. Very large files may use substantial memory because the full file is read into memory.

## License

MIT License. See [LICENSE](./LICENSE) for details.
