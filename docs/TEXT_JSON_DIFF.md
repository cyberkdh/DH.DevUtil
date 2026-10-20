# Text · JSON Diff

[한국어](./TEXT_JSON_DIFF.ko.md)

Text · JSON Diff compares two values locally and shows added, removed, and unchanged lines. JSON mode parses and formats both values before comparison.

## Features

- Compare plain text line by line.
- Parse and format both sides as JSON before comparing.
- Show original and changed line numbers with color-coded additions and removals.
- Load an example, format both inputs, clear, and copy the diff.
- Choose from text, API JSON, configuration JSON, Markdown, and log samples.
- Drag a local file directly onto the `file1` or `file2` editor to load it into either side.
- Switch between Unified, Side-by-side, Inline, Word, Character, Moved lines, Summary, JSON Path, JSON Tree, Patch, and Change heatmap views.
- Ignore whitespace, case, blank lines, comments, JSON property order, or trailing commas; show changed lines only and choose context lines around changes.
- Switch the interface and learning guide between English and Korean.
- Process all values locally in a standalone HTML file.

## How to use

1. Open [Text · JSON Diff](../tools/DH.DevUtil.text-json-diff.html).
2. Choose **Text** for source code, logs, Markdown, or plain text.
3. Choose **JSON** for structured data; invalid JSON is reported before comparison.
4. Read green additions and red removals in the result panel.
5. Drop one file directly into each editor when comparing local files; file contents are read only in the browser.

## Important details

- The current implementation compares lines using a longest common subsequence (LCS) algorithm.
- JSON formatting uses two-space indentation. Property order is preserved, so different property order can appear as a change.
- Before comparison, UTF-8 BOM and CRLF/LF/CR line-ending differences are normalized so identical lines are not reported as changes only because of platform line endings.
- Very large inputs may require more browser memory because the line comparison builds an in-memory table.
- Word and character highlighting is a compact prefix/suffix comparison for changed line pairs. Moved-line detection is heuristic and matches identical line content.

## Privacy

The result view uses a viewport-sized internal scroll area. The page scrollbar is visually hidden while page scrolling remains available through wheel, touch, and keyboard input. The current view can be saved locally as `.txt`; Patch view uses `.patch`.
The Comparison input panel can be collapsed to focus on the result.

All processing happens in the current browser tab. The tool has no server endpoint, external library, upload control, or persistent input storage. The selected interface language may be saved in `localStorage`.
