# JWT Inspector

[English](./JWT_INSPECTOR.md)

JWT Inspector는 [RFC 7519](https://www.rfc-editor.org/rfc/rfc7519) JSON Web Token의 compact 형식을 로컬에서 생성하고 파싱하는 학습용 도구입니다. 서명 생성·검증은 HS256 (HMAC-SHA-256)만 지원합니다.

## 화면 미리보기

![JWT Inspector 화면 미리보기](./images/DH.DevUtil.jwt-inspector.png)

이미지에는 도구 화면 설명을 위한 테스트 값이 포함되어 있습니다. 실제 운영 JWT나 비밀 키를 입력하지 마세요.

## 기능

- Issuer emulation에서 JSON protected header와 claims를 편집해 테스트 JWT 생성
- 브라우저의 암호학적 난수 생성기(CSPRNG)로 256-bit 임시 서명 키 생성
- 생성 JWT 또는 사용자가 붙여 넣은 compact JWS의 header/payload 파싱
- `iss`, `sub`, `aud`, `exp`, `nbf`, `iat`, `jti` 등록 claim을 찾아 표시하고 NumericDate 시간 claim을 UTC로 변환
- HS256 서명 검증 및 `alg` 미지원/불일치 거부
- Parse 상세에서 세그먼트, 디코딩된 Header/Payload, 바이트 길이와 검증 미수행 상태 확인
- Verify 상세에서 signing input, 키 바이트 길이, 기대·수신 signature 및 비교 결과 확인 (키 원문은 표시하지 않음)
- 모든 compact 세그먼트에 정규(canonical) Base64URL 인코딩을 요구
- 네트워크 요청이나 영구 저장 없이 브라우저에서 처리

## 사용 방법

1. 최신 브라우저에서 [JWT Inspector](../tools/DH.DevUtil.jwt-inspector.html)를 엽니다.
2. **Generate · Issuer emulation**에서 **Generate temporary key**를 눌러 임시 키를 만듭니다. Header와 claims는 필요에 따라 JSON으로 수정합니다.
3. Header의 `alg`는 `HS256`이어야 하며, 지원하지 않는 critical extension과 `b64=false` unencoded payload는 거부됩니다. **Generate JWT**를 누르면 HS256 compact JWS가 만들어져 Parser 입력란에 표시됩니다. 생성된 토큰을 자체 임시 키로 검증할 수 있도록 Verify 패널도 채워집니다.
4. 외부 토큰을 확인하려면 Parser 입력란에 붙여 넣고 **Parse token**을 누릅니다. **Show parsing details**를 펼치면 세 segment와 디코딩 과정을 확인할 수 있습니다. 구조와 claim을 읽는 것만으로 서명 유효성이 확인되지는 않습니다.
5. HS256 토큰의 서명을 확인하려면 해당 키를 별도로 **HS256 verification key**에 입력하고 **Verify HS256 signature**를 누릅니다. **Show HS256 verification details**에서 HMAC 입력, 기대·수신 signature와 비교 결과를 볼 수 있습니다. 비밀키 원문은 상세에 노출하지 않습니다.

임시 키를 새로 생성하면 이전 토큰과 파싱·검증 결과를 지워 이전 키로 만든 토큰을 혼동하지 않도록 합니다. 키, Header 또는 claims를 편집하는 것만으로 이미 생성된 토큰이 바뀌지는 않으며, 새 입력을 반영하려면 다시 생성해야 합니다.

## JWT 형식과 검증 의미

일반적인 signed compact JWT (JWS)는 다음 세 부분을 점(`.`)으로 연결합니다.

```text
BASE64URL(protected header).BASE64URL(payload).BASE64URL(signature)
```

Header와 payload는 Base64URL 인코딩이지 암호화(encryption)가 아닙니다. 누구나 내용을 디코딩할 수 있으므로 비밀정보를 payload에 넣지 마세요. 파싱 결과는 토큰의 claims를 보여줄 뿐 신뢰성을 뜻하지 않습니다.

각 세그먼트는 padding bit까지 정규 Base64URL 인코딩이어야 합니다. 디코딩하면 같은 바이트가 되는 비정규 표기는 거부합니다.

서명 검증 성공은 선택한 HS256 key에 대해 서명이 일치했다는 것만 의미합니다. 발급자(`iss`), 대상(`aud`), 만료(`exp`), 정책 또는 사용자 권한을 자동으로 검증하지 않으며, 발급자 신뢰를 보증하지 않습니다. 이 도구는 검증 알고리즘을 토큰의 `alg` 값에 따라 선택하지 않으며, HS256 외 알고리즘과 `alg=none` 서명을 검증하지 않습니다. 이해할 수 없는 critical header extension 및 `b64=false` unencoded payload도 거부합니다.

## 범위 및 보안

이 도구는 JWS compact serialization 파싱, 로컬 HS256 생성·검증까지만 지원합니다. JWE 암호화/복호화, RSA/ECDSA 서명, 실제 Identity Provider 연동, 정책 기반 claims 검증은 지원하지 않습니다. 5개 세그먼트 JWE 형식은 감지해 미지원임을 안내합니다.

**운영 JWT, 개인정보가 포함된 claims, production signing key를 입력하지 마세요.** 입력한 token과 key는 현재 브라우저에서 처리하며 저장·전송하지 않습니다. 생성된 token과 임시 key는 데모용이며 실제 인증에 사용하면 안 됩니다.
