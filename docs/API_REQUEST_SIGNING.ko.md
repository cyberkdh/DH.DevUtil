# API Request Signing Simulator

[English](./API_REQUEST_SIGNING.md)

일반화된 canonical request를 만들고 HMAC-SHA-256으로 로컬 서명합니다.

## 기능

- method, path, query, headers, body 입력.
- SHA-256 payload digest.
- 결정적인 canonical request 미리보기.
- Base64와 hexadecimal signature 출력.

특정 vendor 인증 프로토콜이 아닌 학습용 일반 모델입니다. [API Request Signing Simulator](../tools/DH.DevUtil.api-signing.html)를 열고 운영 secret은 입력하지 마세요.
