# DH.MarkDown.Flow

[English](./MARKDOWN_FLOW.md)

DH.MarkDown.Flow는 로컬 우선(local-first) Markdown 편집기·뷰어입니다. Markdown 원문, WYSIWYG 편집, 브라우저 미리보기를 서로 맞춰 유지하고, 문서를 Markdown, HTML, PDF, Word(DOCX)로 내보냅니다.

## 화면 미리보기

![DH.MarkDown.Flow 화면 미리보기](./images/DH.MarkDown.Flow.png)

## 기능

- **Source**, **WYSIWYG**, **Split** 모드로 편집합니다. Split 모드는 편집기와 미리보기를 좌우(Side by side) 또는 위아래(Stacked)로 배치합니다.
- WYSIWYG에서 편집한 내용을 Markdown 원문으로 다시 저장합니다.
- 도구 모음으로 제목, 굵게, 기울임, 취소선, 인라인 코드, 링크, 참조 링크, 목록, 작업 목록, 인용, 코드 블록, 표, 이미지, 구분선을 넣습니다.
- 지원 Markdown: 제목, setext 제목, 굵게, 기울임, 취소선, 인라인 코드, 링크, 참조 스타일 링크, 이미지, 강제 줄바꿈, 구분선, 인용, 중첩 목록, 작업 목록, 정렬이 있는 표, fenced code, 들여쓰기 코드, tilde fence
- Mermaid 다이어그램을 미리보고 내보냅니다. 좌→우, 우→좌로 긴 파이프라인은 읽기 쉽게 여러 줄로 접습니다.
- Markdown, HTML, PDF, Word(DOCX)로 내보냅니다.
- 미리보기와 문서 내보내기에 함께 쓰는 렌더링 테마를 고르거나 직접 관리합니다.
- 초안을 현재 브라우저에 자동 저장하고, 로컬 파일을 열거나 저장합니다.
- 내장 예제(Comprehensive Markdown, Comprehensive Korean, DOCX Export Test)를 열어 볼 수 있습니다.

## 파일 구성

| 파일 | 용도 |
|---|---|
| [`index.html`](../tools/DH.MarkDown.Flow/index.html) | 웹 빌드. `assets/`를 불러오며 GitHub Pages나 HTTP 서버에서 실행합니다. |
| [`index_local.html`](../tools/DH.MarkDown.Flow/index_local.html) | Chrome이나 Edge에서 `file://`로 바로 여는 단일 파일 빌드(약 5.4MB) |
| [`LICENSE`](../tools/DH.MarkDown.Flow/LICENSE) | MIT License |
| [`THIRD_PARTY_NOTICES.md`](../tools/DH.MarkDown.Flow/THIRD_PARTY_NOTICES.md) | 서드파티 패키지(Mermaid, docx와 그 의존성) 및 샘플 리소스 고지 |

## 사용 방법

1. [온라인 실행](https://cyberkdh.github.io/DH.DevUtil/tools/DH.MarkDown.Flow/index.html)을 열거나, [오프라인 버전](https://raw.githubusercontent.com/cyberkdh/DH.DevUtil/main/tools/DH.MarkDown.Flow/index_local.html)을 내려받아 Chrome 또는 Edge에서 엽니다. 다운로드 링크는 우클릭 후 **다른 이름으로 링크 저장**을 선택하세요. 그냥 클릭하면 저장되지 않고 파일 코드가 화면에 표시됩니다.
2. 편집기에 Markdown을 입력하거나, **Open**으로 로컬 `.md` 파일을 불러옵니다.
3. 필요에 따라 **Source**, **WYSIWYG**, **Split**을 전환합니다. 지원 문법은 **Examples**의 예제에서 확인할 수 있습니다.
4. **Save**로 Markdown 파일을 저장하거나, **Export**로 HTML, PDF, Word 문서를 만듭니다.

`index.html`을 더블클릭해서 열지 마세요. 브라우저가 `file://`에서 불러오는 module 스크립트를 막아 앱이 시작되지 않습니다. 오프라인으로 사용할 때는 `index_local.html`을 여세요.

## 개인정보 및 제한 사항

- 문서는 현재 브라우저에서 처리합니다. 초안은 서버가 아니라 해당 브라우저의 로컬 저장소에 저장되며, 사이트 데이터를 지우면 함께 삭제됩니다.
- 문서가 참조하는 이미지 등 외부 리소스는 미리보기나 내보내기 때 네트워크에서 불러옵니다. CORS와 브라우저 보안 정책에 따라 결과가 달라질 수 있습니다.
- CommonMark나 GitHub Flavored Markdown을 완전히 구현하지는 않습니다. 미리보기 안전을 위해 Raw HTML은 제외하며, 각주, 정의 목록, 일부 복잡한 중첩 강조는 지원하지 않습니다.
- 브라우저 미리보기와 DOCX/PDF 레이아웃은 페이지 나눔과 글꼴 크기 계산이 다를 수 있습니다.
- 매우 크거나 연결이 많은 Mermaid 다이어그램은 테마 조정이 필요할 수 있습니다.

## 라이선스

DH.MarkDown.Flow는 MIT License로 배포합니다. Mermaid, docx 등 서드파티 라이브러리를 포함하므로, 재배포할 때는 `LICENSE`와 `THIRD_PARTY_NOTICES.md`를 함께 포함하세요.
