# 변경 이력 (Changelog)

[English](./CHANGELOG.md)

DH.DevUtil의 주요 변경 사항을 기록합니다. 최신 변경이 위에 표시됩니다.

## [Unreleased]

### 추가

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
