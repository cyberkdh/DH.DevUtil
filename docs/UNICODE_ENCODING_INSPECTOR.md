# Unicode · Encoding Inspector

[한국어](./UNICODE_ENCODING_INSPECTOR.ko.md)

Unicode · Encoding Inspector shows what a string is really made of. It lists every code point with its UTF-8, UTF-16, and CP949 bytes, checks NFC/NFD normalization, finds hidden characters such as zero-width spaces and bidi controls, and previews how the text breaks when it is decoded with the wrong encoding. It also decodes raw bytes so you can find which encoding produced them.

## Screenshot

![Unicode · Encoding Inspector preview](./images/DH.DevUtil.unicode-inspector.png)

## Features

- **Summary**: code points, UTF-16 code units (JavaScript/Java/C# `length`), grapheme clusters, UTF-8, UTF-16, and CP949 byte counts, line endings (CRLF/LF/CR), and normalization state.
- **Findings** with line:column positions:
  - Bidirectional controls such as RLO used in "Trojan Source" attacks (CVE-2021-42574)
  - Invisible characters: zero width space, word joiner, soft hyphen, BOM, Hangul fillers, tag characters
  - Control characters, unusual spaces (NBSP, ideographic space, en/em spaces), and U+FFFD replacement characters
  - Lone surrogates, mixed line endings, and text that is not in NFC (for example decomposed Hangul from macOS)
  - Characters CP949 cannot encode, and syllables in the CP949 extension area that strict EUC-KR lacks (for example `똠`)
- **Revealed text**: the input with spaces, tabs, line breaks, and hidden characters shown as visible markers.
- **Encodings**, each with a copy button: UTF-8, UTF-16LE, UTF-16BE, and CP949 hex, percent-encoding, Base64, JSON/JS escapes, HTML numeric references, and a U+XXXX list.
- **Normalization**: NFC, NFD, NFKC, and NFKD results with their code point counts.
- **Mojibake preview**: UTF-8 read as CP949, CP949 read as UTF-8, UTF-8 read as Windows-1252, and UTF-16LE read as UTF-8.
- **Characters table**: one row per code point with line:column, UTF-8, UTF-16, CP949, general category, script, block, and the initial/medial/final split of each Hangul syllable. Filter to non-ASCII or to hidden and unusual characters only.
- **Bytes mode**: paste hex (`ED 95 9C`, `0xED,0x95`, `\xED\x95`, `%ED%95`) or Base64 and compare the UTF-8, CP949, UTF-16LE/BE, and Windows-1252 decodings. The tool marks which decodings are valid, suggests the most likely one, and **Inspect** sends a decoding to Text mode.
- **Clean hidden characters** removes control, zero-width, bidi, tag, and filler characters and the BOM, and turns unusual spaces into normal spaces. It keeps tabs, line breaks, ZWJ/ZWNJ, and variation selectors because emoji and some scripts need them.
- **Normalize to NFC** composes decomposed text in place.
- **Learn more** explains code points and encodings, why string lengths differ between languages, database column sizes, NFC/NFD, the Hangul composition formula, hidden characters, BOM, mojibake patterns, and EUC-KR versus CP949, in English and Korean.

## How to use

1. Open the [live demo](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.unicode-inspector.html), or download `tools/DH.DevUtil.unicode-inspector.html` and open it in a browser.
2. Paste text into **Text**, or select **Load example** to see every kind of finding at once.
3. Read **Findings** first, then use the **Characters** table to locate each character.
4. If you have raw bytes instead of text, switch to **Bytes**, paste hex or Base64, and select **Inspect** on the decoding that reads correctly.

## Limitations

- Character names come from a built-in list of special characters, the Hangul composition formula, and the browser's Unicode property data. The tool does not include the full Unicode character name database.
- CP949 bytes are built from the browser's `euc-kr` decoder, which implements CP949 (WHATWG Encoding Standard). Results match Windows code page 949, Java `MS949`, and Python `cp949`.
- Grapheme counts use `Intl.Segmenter` and may differ slightly between browser versions.
- Up to 1,000,000 UTF-16 code units are analysed, and the Characters table shows up to 3,000 rows.

## Privacy

Input is processed in the current browser and is not uploaded or stored. Only the Learn more language choice is saved in the browser's local storage.
