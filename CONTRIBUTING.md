# Contributing

Contributions are welcome. Before proposing a change, review the structure of the existing standalone HTML tools and the privacy and validation guidelines below.

[한국어 안내](./CONTRIBUTING.ko.md)

## Guidelines

- Tools should remain dependency-free standalone HTML files by default. If an external library or network request is necessary, explain its purpose and privacy impact first.
- Do not upload or collect user files, JSON input, or hash input data through telemetry.
- Clearly document settings required to compare hash results, such as variants, seeds, endianness, and SHAKE output lengths.
- Warn users not to mistake legacy/insecure algorithms or non-cryptographic checksums for security mechanisms.
- Preserve the existing tool design, responsive layout, and keyboard accessibility.

## Validation

Open the modified HTML in a supported browser and check the following:

1. Confirm that the developer console has no errors.
2. Test valid, empty, and invalid input for the relevant tool.
3. If a hash algorithm changes, compare it against known test vectors and an independent reference implementation.
4. For file tools, test file selection, multiple files and drag/drop, Copy/Delete, output formats, and downloads.
5. Confirm that no external dependency, network request, or sensitive-data logging was introduced.

## Pull Requests

Describe the purpose of the change, user-visible behavior changes, validation performed, and known limitations. For bug fixes, include reproduction steps and expected versus actual results.
