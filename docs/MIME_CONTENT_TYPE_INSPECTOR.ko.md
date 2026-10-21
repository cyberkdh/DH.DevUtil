# MIME · Content-Type Inspector

[English](./MIME_CONTENT_TYPE_INSPECTOR.md)

MIME · Content-Type Inspector는 입력한 `Content-Type` 헤더를 파싱하여 타입, subtype, 구조화 문법 suffix, 매개변수, charset, 텍스트·바이너리 성격, 일반 확장자, 파일명 일치 여부를 설명합니다.

## 기능

- `application/json; charset=utf-8` 같은 미디어 타입 파싱
- JSON, EML, multipart form, PDF 샘플 불러오기
- 선택한 샘플의 대표 raw 원본 표시. RFC 822 형식 EML 헤더와 본문 포함
- top-level type, subtype, `+json`·`+xml` suffix, 매개변수, charset 표시
- 로컬 휴리스틱(heuristic)을 사용한 텍스트 중심·바이너리 중심 분류
- 파일명 확장자와 로컬 MIME 매핑 비교
- 예제, 초기화, 결과 복사, English·한국어 UI 전환
- 독립 실행형 HTML 안에서 모든 값 로컬 처리

## 중요 사항

- 확장자 매핑은 학습용으로 축약한 목록이며 전체 IANA registry가 아닙니다.
- 주요 이메일 매핑으로 `message/rfc822` → `.eml`, `application/vnd.ms-outlook` → `.msg`를 포함합니다.
- Content-Type은 표현 형식을 설명하고 파일명 확장자는 힌트일 뿐입니다.
- 파일 바이트를 검사하거나 실제 파일이 선언된 타입과 일치하는지 검증하지 않습니다.

## 개인정보 보호

모든 처리는 현재 브라우저 탭에서 이루어집니다. 값을 외부로 전송하거나 저장하지 않습니다.
