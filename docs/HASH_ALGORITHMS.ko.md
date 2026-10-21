# 파일 해시 계산기 — 알고리즘 안내

[File Hash Calculator](../tools/DH.DevUtil.hash.html)는 선택한 파일을 브라우저에서 읽고 아래 알고리즘 결과를 표시합니다. 결과는 입력 바이트열, 알고리즘 variant, seed, 출력 길이에 따라 달라집니다.

[English](./HASH_ALGORITHMS.md)

RIPEMD-160도 선택할 수 있습니다. 기존 시스템·파일 형식과의 호환성이 필요한 경우에만 사용하고, 새로운 보안 설계에는 SHA-256 이상을 사용하세요.

![File Hash Calculator](./images/file-hash-calculator.png)

## 암호학적 해시 및 XOF

| 계열 | 알고리즘 | 출력 길이 | 설명 |
|---|---|---:|---|
| SHA-2 | SHA-224 | 224 bit | SHA-256 계열에서 별도 초기 상태를 사용하는 variant |
| SHA-2 | SHA-256 | 256 bit | Web Crypto API 사용 |
| SHA-2 | SHA-384 | 384 bit | Web Crypto API 사용 |
| SHA-2 | SHA-512 | 512 bit | Web Crypto API 사용 |
| SHA-3 | SHA3-224 | 224 bit | Keccak 기반 SHA-3 표준 |
| SHA-3 | SHA3-256 | 256 bit | Keccak 기반 SHA-3 표준 |
| SHA-3 | SHA3-384 | 384 bit | Keccak 기반 SHA-3 표준 |
| SHA-3 | SHA3-512 | 512 bit | Keccak 기반 SHA-3 표준 |
| SHAKE | SHAKE128 (256-bit 출력) | 256 bit | XOF 출력 길이 고정 |
| SHAKE | SHAKE256 (512-bit 출력) | 512 bit | XOF 출력 길이 고정 |

SHAKE는 확장 가능 출력 함수(extendable-output function, XOF)입니다. 이 도구는 파일 결과를 일관되게 비교할 수 있도록 출력 길이를 고정합니다. 다른 출력 길이를 사용하는 SHAKE 결과와는 직접 비교할 수 없습니다.

## 레거시 해시

| 알고리즘 | 출력 길이 | 사용 목적 |
|---|---:|---|
| SHA-1 | 160 bit | 레거시 시스템/파일 형식과의 호환 |
| MD4 | 128 bit | 레거시 호환 |
| MD5 | 128 bit | 레거시 호환 |

SHA-1, MD4, MD5는 암호학적으로 취약하며 신뢰할 수 있는 충돌 저항성을 제공하지 않습니다. 새 보안 설계, 서명, 비밀번호 저장 또는 공격자에 대한 파일 무결성 확인에 사용하지 마세요. 도구에서는 레거시 및 비보안(legacy/insecure) 항목으로 분리합니다.

## 체크섬 및 비암호학 해시

| 분류 | 알고리즘 | 설정 |
|---|---|---|
| CRC | CRC-8/SMBUS | width 8, polynomial `07`, init `00`, xorout `00` |
| CRC | CRC-16/CCITT-FALSE | width 16, polynomial `1021`, init `ffff`, non-reflected |
| CRC | CRC-32/ISO-HDLC | width 32, reflected polynomial `edb88320`, init/xorout `ffffffff` |
| CRC | CRC-64/ECMA-182 | width 64, polynomial `42f0e1eba9ea3693`, init/xorout `0` |
| 체크섬 | Adler-32 | Adler-32 checksum |
| 체크섬 | Fletcher-32 | Big-endian 16-bit word 사용; 입력 길이가 홀수이면 마지막 byte 뒤에 `00` 추가 |
| 비암호학 해시 | FNV-1a 32 | 32-bit |
| 비암호학 해시 | FNV-1a 64 | 64-bit |
| 비암호학 해시 | xxHash32 | seed `0` |
| 비암호학 해시 | xxHash64 | seed `0` |
| 비암호학 해시 | MurmurHash3 x86 32 | seed `0` |
| 비암호학 해시 | CityHash64 | 64-bit variant |
| 비암호학 해시 | FarmHash Fingerprint64 | Fingerprint64 variant |
| 비암호학 해시 | MetroHash64 v1 | version 1, seed `0` |
| 비암호학 해시 | Jenkins One-at-a-time | 32-bit |

비암호학 체크섬과 해시는 우발적인 데이터 변경 검출이나 자료 구조/식별 목적으로 사용합니다. 공격자가 의도적으로 변경하는 상황에서 안전한 검증 방법은 아닙니다. CRC는 같은 폭에도 여러 variant가 있으므로 결과 비교 시 알고리즘 이름과 파라미터가 일치하는지 확인하세요.

## 결과 표현

- 기본 결과는 16진수(Hex)입니다. 파일별로 소문자, 대문자 또는 Base64 표시를 선택할 수 있습니다.
- 표시 형식은 digest byte의 인코딩만 바꾸며 해시 계산 결과는 바꾸지 않습니다.
- 서로 다른 라이브러리의 정수 digest를 비교할 때는 byte order/endian 표기 차이를 확인하세요.

## 범위에서 제외

HMAC은 비밀 키(secret key)를 입력으로 받는 메시지 인증 코드(message authentication code, MAC)이며 일반 파일 해시와 목적 및 UI가 다릅니다. 현재 도구에는 포함되어 있지 않습니다. `realm`은 HMAC 자체의 필수 입력이 아닙니다.
