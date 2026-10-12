# DH.DevUtil

DH.DevUtil is a collection of lightweight utilities for everyday development tasks. Each tool is a standalone HTML file that runs in a modern browser without installation.

[한국어](./README.ko.md)

## Tools

| Tool | What it does | Live demo | Source | Guide |
|---|---|---|---|---|
| JSON Parser | Validate, explore, format, and minify JSON. Inspect Base64 values and preview embedded images. | <a href="https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.json.html" target="_blank" rel="noopener noreferrer">Run</a> | [View source](./tools/DH.DevUtil.json.html) | [Guide](./docs/JSON_PARSER.md) |
| File Hash Calculator | Calculate cryptographic hashes, checksums, and non-cryptographic hashes for local files. | <a href="https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.hash.html" target="_blank" rel="noopener noreferrer">Run</a> | [View source](./tools/DH.DevUtil.hash.html) | [Algorithms and guide](./docs/HASH_ALGORITHMS.md) |
| HMAC Simulator (Base) | Calculate and verify HMAC tags and explore the Client → in-transit data → Server flow. | <a href="https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.hmac-simulator-base.html" target="_blank" rel="noopener noreferrer">Run</a> | [View source](./tools/DH.DevUtil.hmac-simulator-base.html) | [Guide](./docs/HMAC_SIMULATOR.md) |

Live demos run the static HTML tools on GitHub Pages. The source links open the HTML files in GitHub's code viewer; they do not run the tools. To use a tool offline, download its HTML file or clone the repository and open it in a browser.

## Important

- Tools process input in the current browser and do not upload it to a DH.DevUtil server.
- Do not enter production secrets or credentials in HMAC Simulator (Base). It intentionally displays key-derived intermediate values.
- Legacy hashes and non-cryptographic checksums are not suitable for security against malicious changes. See the [hash security notes](./docs/HASH_ALGORITHMS.md).
- When using a downloaded copy or embedding a tool in another page, verify and trust its source and the surrounding browser environment.

## Getting Started

1. Select **Run** in the tool catalog to use a live demo, or clone this repository/download the HTML source for offline use.
2. Follow the corresponding tool guide.

## Recent Changes

See the [changelog](./CHANGELOG.md) for unreleased updates and release history.

## Project

- [Contributing](./CONTRIBUTING.md)
- [Security policy](./SECURITY.md)
- [MIT License](./LICENSE)
