# Vendored AES-CBC module

- Upstream: [@noble/ciphers](https://github.com/paulmillr/noble-ciphers)
- Version: 2.4.0
- License: MIT; see [LICENSE](./LICENSE)
- Package registry: https://www.npmjs.com/package/@noble/ciphers

This folder contains the upstream AES module and its local dependencies, plus a browser IIFE bundle used by the Symmetric Encryption Simulator. The bundle exposes only the AES-CBC `cbc` function. It is loaded from this local folder so the HTML tool works without a CDN or network connection.

AES-CBC padding is selected by the simulator:

- PKCS#7 uses the library's built-in padding.
- ANSI X.923, Zero, and NoPadding are prepared/checked by the simulator and passed to the library with its padding disabled.

The library's CBC implementation is not authenticated encryption. A JavaScript cipher implementation also does not provide the same constant-time guarantees as a platform cryptographic provider. Do not use this educational tool or these unauthenticated modes to protect production data.
