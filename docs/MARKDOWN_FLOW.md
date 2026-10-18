# DH.MarkDown.Flow

[한국어](./MARKDOWN_FLOW.ko.md)

DH.MarkDown.Flow is a local-first Markdown editor and viewer. It keeps Markdown source, WYSIWYG editing, and browser preview in sync, and exports documents to Markdown, HTML, PDF, and Word (DOCX).

## Screenshot

![DH.MarkDown.Flow preview](./images/DH.MarkDown.Flow.png)

## Features

- Edit in **Source**, **WYSIWYG**, or **Split** mode. Split mode can show the editor and preview side by side or stacked.
- Write Markdown back to source after visual editing.
- Use the toolbar for headings, bold, italic, strikethrough, inline code, links, reference links, lists, task lists, quotes, code blocks, tables, images, and horizontal rules.
- Supported Markdown: headings, setext headings, bold, italic, strikethrough, inline code, links, reference-style links, images, hard breaks, horizontal rules, blockquotes, nested lists, task lists, tables with alignment, fenced code, indented code, and tilde fences.
- Preview and export Mermaid diagrams. Long left-to-right and right-to-left pipelines wrap into readable rows.
- Export Markdown, HTML, PDF, and Word (DOCX).
- Choose a rendering theme shared by the preview and document export, or manage your own themes.
- Auto-save drafts in the current browser, and open or save local files.
- Open the built-in examples: Comprehensive Markdown, Comprehensive Korean, and DOCX Export Test.

## Files

| File | Use |
|---|---|
| [`index.html`](../tools/DH.MarkDown.Flow/index.html) | Web build. Loads `assets/` and runs from GitHub Pages or any HTTP server. |
| [`index_local.html`](../tools/DH.MarkDown.Flow/index_local.html) | Standalone single-file build (about 5.4 MB) for opening directly in Chrome or Edge with `file://`. |
| [`LICENSE`](../tools/DH.MarkDown.Flow/LICENSE) | MIT License. |
| [`THIRD_PARTY_NOTICES.md`](../tools/DH.MarkDown.Flow/THIRD_PARTY_NOTICES.md) | Third-party packages (Mermaid, docx, and their dependencies) and sample resources. |

## How to use

1. Open the [live demo](https://cyberkdh.github.io/DH.DevUtil/tools/DH.MarkDown.Flow/index.html), or [download the offline version](https://raw.githubusercontent.com/cyberkdh/DH.DevUtil/main/tools/DH.MarkDown.Flow/index_local.html) and open it in Chrome or Edge. Right-click the download link and choose **Save link as**; a normal click shows the file's code instead of saving it.
2. Type Markdown in the editor, or select **Open** to load a local `.md` file.
3. Switch between **Source**, **WYSIWYG**, and **Split** as needed. Select an item under **Examples** to see the supported syntax.
4. Select **Save** to save the Markdown file, or **Export** to create HTML, PDF, or Word output.

Do not open `index.html` by double-clicking it. Browsers block module scripts loaded from `file://`, so the app does not start. Use `index_local.html` for offline use.

## Privacy and limitations

- Documents are processed in the current browser. Drafts are stored in that browser's local storage, not on a server. Clearing site data deletes them.
- Images and other external resources referenced by a document are loaded from the network when previewed or exported. CORS and browser security policies can affect the result.
- This is not a complete CommonMark or GitHub Flavored Markdown implementation. Raw HTML is excluded for preview safety. Footnotes, definition lists, and some complex nested emphasis cases are not supported.
- Browser preview and DOCX/PDF layout can differ in pagination and font metrics.
- Very large or highly connected Mermaid diagrams may need a theme adjustment.

## License

DH.MarkDown.Flow is distributed under the MIT License. It bundles third-party libraries, including Mermaid and docx. Keep `LICENSE` and `THIRD_PARTY_NOTICES.md` with any copy you redistribute.
