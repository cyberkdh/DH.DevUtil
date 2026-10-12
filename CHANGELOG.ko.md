# 변경 이력 (Changelog)

[English](./CHANGELOG.md)

DH.DevUtil의 주요 변경 사항을 기록합니다. 최신 변경이 위에 표시됩니다.

## [Unreleased]

### 추가

- HMAC-SHA-256/384/512 계산 과정과 Client → 전달 데이터 → Server 검증 흐름을 학습할 수 있는 브라우저 기반 HMAC Simulator (Base) 추가

### 개선

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
