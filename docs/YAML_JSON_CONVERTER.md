# YAML · JSON Converter

[한국어](./YAML_JSON_CONVERTER.ko.md)

YAML · JSON Converter converts common configuration-style YAML and JSON locally in a standalone HTML file.

## Features

- Convert mappings, sequences, nested values, scalar values, and common inline JSON-style values.
- Convert formatted JSON into readable YAML.
- Load configuration, service-list, and nested-data samples.
- Show the selected sample source before conversion.
- Swap input/output direction, clear, and copy the result.
- Switch between English and Korean UI.

## Important details

- The YAML parser is a small educational parser for common configuration files, not a complete YAML 1.2 implementation.
- It does not aim to support anchors, aliases, custom tags, multi-document streams, complex keys, or every block-scalar rule.
- Use a full YAML library when exact compatibility with arbitrary YAML documents is required.

## Privacy

All processing happens in the current browser tab. No value is uploaded or stored.
