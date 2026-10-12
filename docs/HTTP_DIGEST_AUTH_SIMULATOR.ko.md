# HTTP Digest Authentication Simulator

[English](./HTTP_DIGEST_AUTH_SIMULATOR.md)

HTTP Digest Authentication Simulator는 [RFC 7616](https://www.rfc-editor.org/rfc/rfc7616)의 challenge-response 흐름을 학습하는 독립형 브라우저 도구입니다.

## 화면 미리보기

![HTTP Digest Authentication Simulator 화면 미리보기](./images/DH.DevUtil.http-digest-auth-simulator.png)

## 기능

- Server challenge, Client response, Server verification을 세 개의 패널에서 시뮬레이션
- RFC 7616의 여섯 algorithm 토큰 선택: `MD5`, `MD5-sess`, `SHA-256`, `SHA-256-sess`, `SHA-512-256`, `SHA-512-256-sess`
- `qop=auth` 응답 계산 및 `-sess`의 별도 HA1 계산 적용
- HA1, HA2, response 입력 문자열과 계산값 확인
- 검증 후 성공·실패와 관계없이 Server가 입력받은 계정 자격 증명으로 재계산한 HA1, HA2, 기대 response 확인
- HTTP `Authorization: Digest` 헤더 표시 및 수정 가능한 로컬 JSON 표현을 verifier로 전달
- `userhash=true` 선택 가능. Client는 `H(username:realm)`을 전송하며 Server는 별도로 입력한 계정 User ID로 검증
- RFC 7616 Section 3.9.1 입력 예제 제공
- 브라우저 암호학적 난수 생성기로 256-bit nonce 생성
- UTF-8 입력과 username/password의 Unicode NFC 정규화
- 로컬 MD5 및 SHA-512/256 구현을 시작 시 알려진 정답(known-answer)으로 검사하고, SHA-256은 Web Crypto API로 계산
- 네트워크 요청, 외부 라이브러리, 영구 저장 없이 현재 브라우저에서 처리

## 사용 방법

1. 최신 브라우저에서 [`DH.DevUtil.http-digest-auth-simulator.html`](../tools/DH.DevUtil.http-digest-auth-simulator.html)을 엽니다.
2. **Server · Challenge**에서 알고리즘을 고르고 realm, nonce, 선택적 opaque, `qop=auth`를 설정합니다.
3. Client username, password, method, request URI, nonce count, client nonce를 입력합니다.
4. **Calculate response**를 선택합니다. 생성된 `Authorization` 헤더와 HA1/HA2 계산 과정을 확인할 수 있습니다.
5. **Server · Verify**에서 Server 계정 User ID와 password를 순서대로 입력합니다. `userhash`가 꺼져 있으면 User ID를 비워 둘 수 있지만, 켜져 있으면 원래 계정 User ID가 필요합니다. 수신 데이터를 검증한 뒤 **Show Server verification calculation steps**를 펼치면 성공·실패 모두에서 Server 측 계산 과정을 확인할 수 있습니다. JSON packet을 수정해 변조·실패 상황을 확인할 수 있습니다.
6. **Load RFC 7616 example**으로 Section 3.9.1의 MD5 예제 값을 불러옵니다. challenge 알고리즘을 SHA-256으로 바꾸고 다시 계산해 같은 RFC 예제의 SHA-256 결과도 비교할 수 있습니다.

## Digest 계산

`qop=auth`일 때 다음과 같이 계산합니다.

```text
HA1 = H(username ":" realm ":" password)
HA1-sess = H(HA1 ":" nonce ":" cnonce)
HA2 = H(method ":" request-uri)
response = H(HA1 ":" nonce ":" nc ":" cnonce ":" qop ":" HA2)
```

`-sess` 토큰은 response 계산에 `HA1-sess`를 사용하고, 나머지는 기본 `HA1`을 사용합니다. `userhash=true`이면 Authorization header에 보내는 username은 추가로 `H(username ":" realm)`으로 계산하지만, HA1에는 원래 계정 username을 사용합니다. Digest 값은 소문자 16진수입니다. `SHA-512-256`은 자체 초기 상태(initial state)를 갖는 SHA-512/256 변형이며 SHA-512 결과를 단순히 자른 것이 아닙니다.

## 범위 및 보안

현재 도구는 `qop=auth`만 지원합니다. `auth-int`, `username*`, `Authentication-Info`/`rspauth`, 서버 nonce 유효성·재사용 추적, 실제 HTTP 요청은 구현하지 않습니다. Challenge는 UTF-8 semantics를 표시하며, hashing 전에 username과 password를 NFC로 정규화합니다. 그 밖의 국제화 및 HTTP parsing 동작은 도구 범위에서 제외됩니다.

HTTP Digest Authentication은 오프라인 password 추측 공격에 취약하며 TLS를 대체하지 않습니다. MD5는 RFC 7616 algorithm 토큰 중 하나이므로 학습을 위해 포함했을 뿐, 신규 보안 설계에 권장한다는 의미는 아닙니다. **예제용 자격 증명만 사용하고 운영 password나 secret은 입력하지 마세요.** 페이지는 입력을 저장하거나 전송하지 않지만 브라우저 확장, 주입된 script 또는 수정된 사본은 입력값에 접근할 수 있습니다. 이 verifier는 학습용이며 운영 인증 서버가 아닙니다.
