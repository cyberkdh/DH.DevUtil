# Unicode · Encoding Inspector

[English](./UNICODE_ENCODING_INSPECTOR.md)

Unicode · Encoding Inspector는 문자열이 실제로 무엇으로 이루어져 있는지 보여 줍니다. 모든 코드 포인트(code point)를 UTF-8, UTF-16, CP949 바이트와 함께 나열하고, NFC/NFD 정규화(normalization)를 확인하며, 폭 없는 공백(zero-width space)이나 양방향(bidi) 제어 문자 같은 숨은 문자를 찾고, 잘못된 인코딩으로 읽었을 때 글자가 어떻게 깨지는지 미리 보여 줍니다. 바이트를 디코딩해 어떤 인코딩으로 만들어졌는지 찾을 수도 있습니다.

## 화면 미리보기

![Unicode · Encoding Inspector 화면 미리보기](./images/DH.DevUtil.unicode-inspector.png)

## 기능

- **Summary**: 코드 포인트 수, UTF-16 코드 유닛 수(JavaScript/Java/C# `length`), 그래핌 클러스터(grapheme cluster) 수, UTF-8·UTF-16·CP949 바이트 수, 줄바꿈(CRLF/LF/CR), 정규화 상태
- **Findings**: 줄:열(line:col) 위치와 함께 표시
  - "Trojan Source" 공격(CVE-2021-42574)에 쓰이는 RLO 등 양방향 제어 문자
  - 보이지 않는 문자: 폭 없는 공백, word joiner, soft hyphen, BOM, 한글 채움 문자(filler), 태그 문자(tag character)
  - 제어 문자, 특이한 공백(NBSP, 전각 공백, en/em space), U+FFFD 대체 문자(replacement character)
  - 외톨이 서로게이트(lone surrogate), 섞인 줄바꿈, NFC가 아닌 텍스트(예: macOS의 분해형 한글)
  - CP949로 표현할 수 없는 문자, 엄격한 EUC-KR에는 없는 CP949 확장 영역 음절(예: `똠`)
- **Revealed text**: 공백, 탭, 줄바꿈, 숨은 문자를 눈에 보이는 표시로 바꿔 보여 줍니다.
- **Encodings**: UTF-8, UTF-16LE, UTF-16BE, CP949 16진수, 퍼센트 인코딩(percent-encoding), Base64, JSON/JS 이스케이프, HTML 숫자 참조, U+XXXX 목록을 각각 복사 버튼과 함께 제공합니다.
- **Normalization**: NFC, NFD, NFKC, NFKD 결과와 각각의 코드 포인트 수
- **Mojibake preview**: UTF-8을 CP949로, CP949를 UTF-8로, UTF-8을 Windows-1252로, UTF-16LE를 UTF-8로 읽었을 때의 결과
- **Characters 표**: 코드 포인트마다 한 줄로 줄:열, UTF-8, UTF-16, CP949, 일반 범주(general category), 문자 체계(script), 블록, 한글 음절의 초성·중성·종성 분해를 보여 줍니다. 비ASCII 문자만 또는 숨은·특이 문자만 걸러 볼 수 있습니다.
- **Bytes 모드**: 16진수(`ED 95 9C`, `0xED,0x95`, `\xED\x95`, `%ED%95`)나 Base64를 붙여 넣고 UTF-8, CP949, UTF-16LE/BE, Windows-1252 디코딩 결과를 비교합니다. 유효한 디코딩을 표시하고 가장 가능성 높은 인코딩을 제안하며, **Inspect**로 해당 디코딩 결과를 Text 모드로 보냅니다.
- **Clean hidden characters**: 제어, 폭 없는, 양방향, 태그, 채움 문자와 BOM을 지우고 특이한 공백을 일반 공백으로 바꿉니다. 이모지와 일부 문자 체계에 필요한 탭, 줄바꿈, ZWJ/ZWNJ, 이체자 선택자(variation selector)는 남깁니다.
- **Normalize to NFC**: 분해형 텍스트를 그 자리에서 조합형으로 바꿉니다.
- **Learn more**: 코드 포인트와 인코딩, 언어마다 문자열 길이가 다른 이유, DB 컬럼 크기, NFC/NFD, 한글 조합 공식, 숨은 문자, BOM, 글자 깨짐 패턴, EUC-KR과 CP949의 차이를 영어와 한국어로 설명합니다.

## 사용 방법

1. [온라인 실행](https://cyberkdh.github.io/DH.DevUtil/tools/DH.DevUtil.unicode-inspector.html)을 열거나, `tools/DH.DevUtil.unicode-inspector.html`을 내려받아 브라우저에서 엽니다.
2. **Text**에 텍스트를 붙여 넣거나, **Load example**로 모든 종류의 Findings를 한 번에 확인합니다.
3. 먼저 **Findings**를 읽고, **Characters** 표에서 각 문자의 위치를 찾습니다.
4. 텍스트 대신 원본 바이트가 있다면 **Bytes**로 바꾸고 16진수나 Base64를 붙여 넣은 뒤, 올바르게 읽히는 디코딩에서 **Inspect**를 선택합니다.

## 제한 사항

- 문자 이름은 내장 특수 문자 목록, 한글 조합 공식, 브라우저의 Unicode 속성 데이터로 만듭니다. 전체 Unicode 문자 이름 데이터베이스는 포함하지 않습니다.
- CP949 바이트는 브라우저의 `euc-kr` 디코더로 만듭니다. 이 디코더는 CP949를 구현하므로(WHATWG Encoding Standard) 결과가 Windows 코드 페이지 949, Java `MS949`, Python `cp949`와 같습니다.
- 그래핌 수는 `Intl.Segmenter`를 사용하므로 브라우저 버전에 따라 조금 다를 수 있습니다.
- 최대 1,000,000 UTF-16 코드 유닛까지 분석하고, Characters 표는 최대 3,000줄까지 표시합니다.

## 개인정보

입력은 현재 브라우저에서 처리하며 업로드하거나 저장하지 않습니다. Learn more의 언어 선택만 브라우저 로컬 저장소에 저장합니다.
