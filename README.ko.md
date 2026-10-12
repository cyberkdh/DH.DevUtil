# DH.DevUtil

DH.DevUtil은 일상적인 개발 작업에 사용하는 가벼운 유틸리티 모음입니다. 각 도구는 설치 없이 최신 브라우저에서 실행되는 독립 HTML 파일로 제공됩니다.

[English](./README.md)

## 도구 목록

| 도구 | 기능 | 실행 | 안내 |
|---|---|---|---|
| JSON Parser | JSON 검증·탐색·형식화·축약, Base64 값 확인 및 내장 이미지 미리보기 | [도구 열기](./tools/DH.DevUtil.json.html) | [사용 안내](./docs/JSON_PARSER.ko.md) |
| File Hash Calculator | 로컬 파일의 암호학적 해시, 체크섬 및 비암호학 해시 계산 | [도구 열기](./tools/DH.DevUtil.hash.html) | [알고리즘 및 사용 안내](./docs/HASH_ALGORITHMS.ko.md) |
| HMAC Simulator (Base) | HMAC 태그를 계산·검증하고 Client → 전달 데이터 → Server 흐름을 확인 | [도구 열기](./tools/DH.DevUtil.hmac-simulator-base.html) | [사용 안내](./docs/HMAC_SIMULATOR.ko.md) |

## 중요 안내

- 도구 입력은 현재 브라우저에서 처리하며 DH.DevUtil 서버로 업로드하지 않습니다.
- HMAC Simulator (Base)는 키에서 파생된 중간값을 의도적으로 표시하므로 운영 비밀 키나 자격 증명을 입력하지 마세요.
- 레거시 해시와 비암호학 체크섬은 악의적인 변경에 대한 보안 용도로 적합하지 않습니다. [해시 보안 안내](./docs/HASH_ALGORITHMS.ko.md)를 확인하세요.
- 내려받은 사본을 실행하거나 다른 페이지에 도구를 삽입할 때는 도구 파일의 출처와 브라우저 환경을 신뢰할 수 있는지 확인하세요.

## 시작하기

1. 저장소를 clone하거나 필요한 도구의 HTML 파일을 내려받습니다.
2. 최신 브라우저에서 `tools` 폴더의 파일을 열고 해당 안내 문서를 참고합니다.

## 최근 변경 사항

미출시 변경과 정식 버전 이력은 [변경 이력](./CHANGELOG.ko.md)을 참고하세요.

## 프로젝트 문서

- [기여 안내](./CONTRIBUTING.ko.md)
- [보안 정책](./SECURITY.ko.md)
- [MIT License](./LICENSE)
