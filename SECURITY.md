# Security Policy

[한국어 안내](./SECURITY.ko.md)

## Scope

DH.DevUtil is a collection of standalone browser-based developer utilities. Security reports about these tools and their handling of local input are welcome.

## Reporting a Vulnerability

Please do not publish sensitive proof-of-concept data or real user files in a public issue. If GitHub private vulnerability reporting is enabled for this repository, use it. Otherwise, contact the repository maintainer privately through a channel listed on the maintainer's GitHub profile.

Include the affected tool/file, browser and version, impact, and minimal reproduction steps. Use synthetic or non-sensitive input where possible.

## Data Handling

The File Hash Calculator is designed to process selected files in the browser without uploading them. Do not include secrets or private files in a security report unless absolutely necessary; a small synthetic reproducer is preferred.

## Cryptographic Limitations

SHA-1, MD4, and MD5 are available only for legacy compatibility and are not suitable for security-sensitive use. CRC and other non-cryptographic checksums/hashes do not provide protection against malicious modification.
