# MIME · Content-Type Inspector

[한국어](./MIME_CONTENT_TYPE_INSPECTOR.ko.md)

MIME · Content-Type Inspector parses a local `Content-Type` header and explains its type, subtype, structured syntax suffix, parameters, charset, text/binary nature, common extensions, and filename match.

## Features

- Parse media types such as `application/json; charset=utf-8`.
- Load JSON, EML, multipart form, and PDF examples.
- Show the representative raw source for the selected sample, including RFC 822-style EML headers and body.
- Show top-level type, subtype, `+json`/`+xml` suffix, parameters, and charset.
- Classify the value as text-oriented or binary-oriented using local heuristics.
- Compare a filename extension with common local MIME mappings.
- Load an example, clear input, copy the inspection result, and switch between English and Korean.
- Process all values locally in a standalone HTML file.

## Important details

- The extension mapping is a compact educational mapping, not a complete IANA registry.
- Common email mappings include `message/rfc822` → `.eml` and `application/vnd.ms-outlook` → `.msg`.
- Content-Type describes a representation format; a filename extension is only a hint.
- The tool does not inspect file bytes or validate that a file actually matches the declared type.

## Privacy

All processing happens in the current browser tab. No value is uploaded or stored.
