# Third-Party Notices

DH.MarkDown.Flow is distributed under the MIT License in `LICENSE`. This file records third-party packages used by the project and the external resources referenced by the Markdown samples.

## Direct runtime dependencies

| Package | Version | License | Source |
|---|---:|---|---|
| mermaid | 12.2.0 | MIT | https://github.com/mermaid-js/mermaid |
| docx | 9.7.1 | MIT | https://github.com/dolanmiu/docx |

The package license values and versions above were checked against the installed package manifests and `package-lock.json` on 2026-10-18. The corresponding package `LICENSE` files are included in the local npm installation and should be reviewed again after dependency upgrades.

## Runtime transitive dependencies with non-MIT or multiple-license declarations

| Package | Version | License |
|---|---:|---|
| @chevrotain/* and chevrotain | 13.2.0 | Apache-2.0 |
| d3 and d3-* packages | 3.x–7.x | ISC or BSD-3-Clause |
| d3-sankey | 0.12.3 | BSD-3-Clause |
| dompurify | 3.4.17 | MPL-2.0 OR Apache-2.0 |
| elkjs | 0.9.3 | EPL-2.0 |
| entities | 6.0.1 | BSD-2-Clause |
| jszip | 3.10.2 | MIT OR GPL-3.0-or-later |
| pako | 1.0.11 | MIT AND Zlib |
| robust-predicates | 3.0.3 | Unlicense |
| rw | 1.3.3 | BSD-3-Clause |
| sax | 1.6.1 | BlueOak-1.0.0 |
| saxes | 6.0.0 | ISC |
| source-map-js | 1.2.2 | BSD-3-Clause |
| tough-cookie | 5.1.2 | BSD-3-Clause |
| webidl-conversions | 7.0.0 | BSD-2-Clause |
| xml-name-validator | 5.0.0 | Apache-2.0 |

The package-specific version and license inventory is maintained by `package-lock.json`. Development-only packages such as Playwright, TypeScript, and fake-indexeddb are not included in the standalone application bundle but remain subject to their own licenses.

## Sample external resources

The sample documents reference remote resources for rendering and fallback tests. These resources are not redistributed as local assets by this project.

- Our World in Data charts and data: generally CC BY unless a chart identifies a third-party source or different license. Attribution and the source-specific license must be retained when reusing the data. See https://ourworldindata.org/faqs and https://ourworldindata.org/about.
- Wikimedia Commons `World_map.svg`: the referenced file page identifies the file as public domain. See https://commons.wikimedia.org/wiki/File:World_map.svg.
- World Bank API data: the sample links to the API and source pages; the license and attribution requirements of the specific dataset remain applicable. See https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structures.
- CommonMark specification: referenced as documentation, not bundled content. See https://spec.commonmark.org/current/.

## Notice maintenance

When a dependency or sample URL changes, recheck the package's actual `LICENSE` file or the source provider's current license page and update this notice before publishing a new release.
