# 변경 이력 (Changelog)

[English](./CHANGELOG.md)

DH.DevUtil의 주요 변경 사항을 기록합니다. 최신 변경이 위에 표시됩니다.

## [Unreleased]

### 추가

- TOTP/HOTP Simulator, UUID/ULID Inspector, URL/Query Parser, Cron Explainer, Asymmetric Cryptography Simulator, generic API Request Signing Simulator를 독립 실행형 local HTML 도구로 추가하고 영문/한국어 안내 문서를 제공했습니다.
- File Hash Calculator에 기존 형식 호환용 legacy algorithm인 RIPEMD-160을 추가했습니다.
- PEM · ASN.1 · X.509 Viewer에 PEM/DER 인증서 파일 선택과 editor 직접 drag-and-drop을 추가하고 버튼 hover/focus 대비를 보강했습니다.
- JKS certificate chain의 첫 인증서 추출과 PKCS#12/PFX 외부 ASN.1 구조 검사를 추가했으며 private-key material은 표시하지 않습니다.

- IPv4 네트워크·마스크·호스트 범위·이진수·서브넷 분할을 계산하는 CIDR Calculator와 English·한국어 UI를 추가했습니다.
- salt, PBKDF2, 반복 횟수, 키 길이, 비밀번호 검증을 브라우저에서 학습하는 Password Hashing Lab과 영문·한국어 안내 문서를 추가했습니다.
- Content-Type 파싱, 매개변수·suffix·charset·확장자 힌트를 확인하는 MIME · Content-Type Inspector와 영문·한국어 안내 문서를 추가했습니다.
- 일반적인 설정용 YAML·JSON 변환, 샘플, 영문·한국어 UI를 제공하는 YAML · JSON Converter와 안내 문서를 추가했습니다.
- YAML·JSON 샘플을 변환 전 원본으로 별도 표시하도록 개선했습니다.
- PEM·DER 파싱, ASN.1 트리, 주요 인증서 필드를 제공하는 PEM · ASN.1 · X.509 Viewer와 영문·한국어 안내 문서를 추가했습니다.
- Password Hashing Lab에 두 비밀번호 입력란을 표시하는 `비밀번호 표시` 옵션을 추가했습니다.

- 일반 텍스트·JSON 줄 비교, JSON 형식화, 색상별 추가·삭제 표시, 영문·한국어 UI와 화면 미리보기를 제공하는 Text · JSON Diff를 추가했습니다.
- Text · JSON Diff에 기본 텍스트, API JSON, 설정 JSON, Markdown, 로그 샘플과 로컬 file1/file2 drag-and-drop 불러오기를 추가했습니다.
- file1/file2 별도 drop 영역 대신 editor textarea 자체를 drag-and-drop 대상으로 개선했습니다.
- Text · JSON Diff 비교 전에 UTF-8 BOM과 CRLF/LF/CR 줄바꿈을 정규화하도록 개선했습니다.
- Text · JSON Diff에 Unified·좌우 비교·Inline·JSON Path 보기, 공백·대소문자 무시, 변경 부분만 표시, 문맥 줄 수 선택을 추가했습니다.
- Text · JSON Diff에 Word·Character·이동 줄·요약·JSON Tree·Patch·변경 히트맵 보기와 빈 줄·주석·속성 순서·끝 쉼표 무시 옵션을 추가했습니다.
- Diff result를 창 높이에 맞춘 내부 스크롤 영역으로 표시하고 현재 Diff 보기를 로컬 파일로 저장하는 기능을 추가했습니다.
- 페이지 이동 기능은 유지하면서 페이지 scrollbar를 화면에서 숨겨 Diff result scrollbar가 주로 보이도록 개선했습니다.
- Comparison input 패널에 접기·펼치기 기능을 추가했습니다.
- HEX, RGB, HSL, HSV, OKLCH 변환, 색상 미리보기, WCAG 대비율 검사, 영문·한국어 학습 설명을 제공하는 Color Converter를 추가했습니다.
- ISO 8601, Unix 초·밀리초·마이크로초·나노초, Windows FILETIME, .NET Ticks 변환과 calendar duration 연산을 제공하는 Timestamp Converter를 추가했습니다. 영문·한국어 안내 문서와 화면 미리보기를 포함합니다.
- match, 번호·이름이 있는 capture group, index, replacement preview, 예제와 정규식 flavor 설명을 제공하는 브라우저 로컬 JavaScript `RegExp` 학습 도구 Regex Tester 추가. 영문·한국어 안내 문서와 화면 미리보기 포함
- 코드 포인트, UTF-8/UTF-16/CP949 바이트, 그래핌 수, NFC/NFD/NFKC/NFKD 결과, 줄:열 위치가 포함된 숨은 문자(폭 없는 문자, 양방향 제어 문자, BOM, 특이한 공백, 외톨이 서로게이트) 탐지, 글자 깨짐 미리보기, 한글 초성·중성·종성 분해가 포함된 문자 표를 제공하는 Unicode · Encoding Inspector 추가. Bytes 모드는 16진수·Base64를 UTF-8, CP949, UTF-16LE/BE, Windows-1252로 디코딩. 영문·한국어 안내 문서, README 항목, 화면 미리보기 추가
- Source·WYSIWYG·Split 편집, Mermaid 다이어그램 미리보기, 렌더링 테마, Markdown/HTML/PDF/Word 내보내기를 지원하는 로컬 우선 Markdown 편집기 DH.MarkDown.Flow 추가. 웹 빌드(`index.html`)와 단일 파일 빌드(`index_local.html`)를 라이선스·서드파티 고지와 함께 제공하고, 영문·한국어 안내 문서, README 항목, 화면 미리보기 추가
- E 표기, 10의 거듭제곱, 자릿수 구분자, 16진/2진/8진, 16진 실수 입력을 정확한 일반 표기, 천 단위 구분, 과학적 표기, 공학 표기, SI 접두어, 한국어 단위로 바꾸고, IEEE 754 double/float32 실제 저장값, 2<sup>53</sup> − 1 초과 정수 및 Excel 15자리 한계 경고, 영어·한국어 설명을 제공하는 Number Notation Converter 추가
- AES, ARIA, 3DES, DES(ECB, CBC)와 PKCS#7, ANSI X.923, ISO/IEC 7816-4, Zero, No padding, Encrypt/Decrypt가 함께 쓰는 공유 Key/IV 패널, 재현 가능한 고정 IV, 단계별 상세, IV·padding 동작 설명, NIST/RFC 5794/DES 테스트 벡터를 제공하는 외부 라이브러리 없는 학습 도구 Symmetric Encryption Simulator (Base) 추가
- 영문·한국어 README와 Symmetric Encryption Simulator (Base), Symmetric Encryption Simulator 안내 문서에 화면 미리보기 추가, Symmetric Encryption Simulator 안내 문서에 Base 안내 링크 추가
- RFC 7616의 여섯 algorithm 토큰과 `qop=auth`를 지원하는 로컬 HTTP Digest Authentication challenge-response·검증 학습 도구 추가
- RFC 7616 `userhash=true` 지원
- 로컬에서 테스트 JWT를 생성(HS256)하고 compact JWT를 파싱·검증하는 JWT Inspector 추가
- 영문·한국어 README와 JWT Inspector 안내 문서에 화면 미리보기 추가
- AES-GCM/CBC/CTR 암복호화와 AES-CBC 패딩 비교를 위한 Symmetric Encryption Simulator 추가. AES-CBC는 HTML 안의 JavaScript AES 구현으로 동작해 외부 라이브러리가 필요 없음
- 영문·한국어 README와 HTTP Digest Simulator 안내 문서에 도구 스크린샷 추가
- HMAC-SHA-256/384/512 계산 과정과 Client → 전달 데이터 → Server 검증 흐름을 학습할 수 있는 브라우저 기반 HMAC Simulator (Base) 추가
- 영문·한국어 HMAC 안내 문서에 HMAC Simulator 스크린샷 추가

### 개선

- YAML · JSON Converter 버튼의 hover 대비와 active 피드백을 개선했습니다.
- Color Converter의 대비 미리보기를 한 문장에서 제목·본문·링크·버튼·입력창을 포함한 작은 실제 UI 미리보기로 확장했습니다.
- 데스크톱에서 Color Converter의 WCAG 입력·결과를 왼쪽, 미리보기를 오른쪽에 배치하고 작은 글자·본문·큰 글자·제목 샘플을 추가했습니다.
- 위에서 선택한 색상을 WCAG 전경색·배경색에 적용하거나 두 대비 색상을 교체하는 버튼을 추가했습니다.
- WCAG 전경색·배경색에 적용할 수 있는 흑백 최적 대비색과 Hue 유지 AA/AAA 추천 옵션을 추가했습니다.
- 목표 대비율 선택, 중립 회색 추천, Primary·Surface·Dark·Canvas 기반 추천 팔레트를 추가했습니다.
- 추천 팔레트에 현재 Foreground·Background를 함께 표시하고, 오른쪽 미리보기에도 추천 대조색을 표시하도록 개선했습니다.
- 각 추천 색상을 실제 상대 Foreground 또는 Background 색상 위에 표시하는 조합 sample box를 추가했습니다.
- 모든 추천 팔레트 박스 안에 상대 색상의 이름과 HEX 값을 표시하도록 개선했습니다.
- Timestamp Converter의 local date/time을 선택한 UI locale로 표시하도록 개선했습니다. 한국어 UI에서는 한국식 날짜와 오전·오후 형식을 사용하고 ISO 결과는 표준 형식을 유지합니다.
- native `datetime-local` 컨트롤 아래에 선택한 날짜·시간을 현재 UI 언어로 표시하는 preview를 추가했습니다.
- 14개 lesson Regex Guide를 Regex Tester 페이지 안에 통합했습니다. 가이드 버튼은 페이지 내 lesson으로 이동하고 각 샘플은 새 문서 없이 현재 Tester 입력값으로 불러옵니다.
- 통합 Regex Guide를 내부 modal popup으로 표시하고 닫기 버튼, 배경 클릭, Escape 키 닫기, 원래 버튼으로 focus 복귀를 지원합니다.
- 통합 Regex Guide를 URL, UUID, IPv4, SemVer, 색상, 파일명, JSON, CSV, HTML, Markdown, 환경 변수, SQL parameter, 날짜, 시간 등을 포함한 33개 샘플로 확장했습니다.
- Regex Tester에 flag, 예제, 상태 메시지, match 상세를 포함한 전체 English·한국어 UI 전환과 한국어 화면 미리보기를 추가했습니다.
- Regex Tester에 JavaScript, Python, .NET, Java, PCRE2, Rust별 pattern·flag 표현과 matching API 차이를 보여주는 언어별 정규식 미리보기를 추가했습니다.
- 단계별 문법, 실전 예제, 성능 주의 사항, English·한국어 UI, Tester 연결 버튼을 제공하는 독립 실행형 Regex 학습 가이드를 추가했습니다.
- JWT Inspector에 Parse 세그먼트 디코딩 과정과 HS256 서명 검증 상세 표시 추가
- Symmetric Encryption Simulator에서 AES-CBC PKCS#7, ANSI X.923, Zero, NoPadding 선택 지원
- HTTP Digest Authentication Simulator에서 검증 성공·실패 모두 Server 측 계산 상세를 표시
- GitHub가 README 링크의 새 탭 속성을 제거하므로 Ctrl+클릭으로 새 탭을 여는 방법을 안내
- README에 GitHub Pages 온라인 실행 링크를 추가하고 소스 링크와 구분
- GitHub 코드 뷰어는 HTML을 실행하지 않는다고 안내
- JSON Parser에서 끝 패딩이 없는 유효한 Base64 값을 인식하고, 잘못된 Base64 데이터의 디코딩 실패 원인을 표시
- 내장 이미지 데이터를 검증한 뒤 미리보기 성공 여부를 표시하고, 손상되었거나 지원하지 않는 이미지는 오류로 안내

## [1.0.0] - 2026-10

저장소의 첫 공개 버전입니다.

### JSON Parser

- JSON 문법 검증과 오류, root type, 값/멤버 수, 중첩 깊이, 입력 크기 표시
- 접고 펼칠 수 있는 트리 및 JSON 텍스트 보기, 형식화, 축약, 결과 복사
- Base64 값을 Base64, Hex, C# `byte[]`, C++ `unsigned char` 배열로 확인
- 인식 가능한 Base64 이미지 미리보기 및 다운로드

### File Hash Calculator

- 여러 로컬 파일을 선택하거나 끌어 놓아 다음 28개 알고리즘 계산:
  - SHA-2: SHA-224, SHA-256, SHA-384, SHA-512
  - SHA-3: SHA3-224, SHA3-256, SHA3-384, SHA3-512
  - SHAKE: SHAKE128 (256-bit 출력), SHAKE256 (512-bit 출력)
  - 레거시: SHA-1, MD4, MD5
  - CRC: CRC-8/SMBUS, CRC-16/CCITT-FALSE, CRC-32/ISO-HDLC, CRC-64/ECMA-182
  - 체크섬: Adler-32, Fletcher-32
  - 비암호학 해시: FNV-1a 32/64, xxHash32/64, MurmurHash3 x86 32, CityHash64, FarmHash Fingerprint64, MetroHash64 v1, Jenkins One-at-a-time 32
- 파일별 소문자 Hex, 대문자 Hex, Base64 출력 형식 선택 및 개별 결과 복사·삭제
- 모든 결과 복사 또는 UTF-8 텍스트 파일로 저장

### 저장소

- 영문 문서와 한국어 번역, 기여 및 보안 정책, MIT License 추가
