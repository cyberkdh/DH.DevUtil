# PEM · ASN.1 · X.509 Viewer

[한국어](./PEM_ASN1_X509_VIEWER.ko.md)

PEM · ASN.1 · X.509 Viewer decodes PEM or DER hexadecimal input locally, displays the ASN.1 tree, and extracts common X.509 certificate fields when the input is a certificate.

## Features

- Accept PEM text or DER hexadecimal bytes.
- Load `.pem`, `.crt`, `.cer`, or `.der` files with the file picker, drop zone, or directly onto the editor.
- Display nested ASN.1 tags, lengths, OIDs, strings, and byte previews.
- Extract common certificate fields: serial, issuer, subject, validity, signature algorithm, and public-key algorithm.
- Load a small ASN.1 structure sample, inspect, clear, and copy the summary.
- Load JKS files and extract the first certificate from a certificate chain.
- Load PFX/P12 files and inspect the outer PKCS#12 ASN.1 structure locally.
- Switch between English and Korean UI.
- Button hover and focus states remain high-contrast for keyboard and pointer use.

## Important details

- The built-in sample is a small ASN.1 DER structure, not a signed production certificate.
- This is a local structure viewer and educational inspector. It is not a complete certificate chain, trust, revocation, hostname, or signature validator.
- PEM labels are decoded as Base64 DER bytes; the viewer does not trust a certificate merely because it is syntactically valid.
- JKS private-key material is never displayed. PFX/P12 encrypted safe contents are shown structurally but are not decrypted; enter such files only when that limitation is acceptable.

## Privacy

All processing happens in the current browser tab. No certificate is uploaded or stored.
