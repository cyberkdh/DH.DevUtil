# TOTP / HOTP Simulator

[English](./TOTP_HOTP_SIMULATOR.md)

브라우저의 Web Crypto API로 일회용 비밀번호(OTP)를 로컬에서 생성합니다.

## 기능

- TOTP와 HOTP 모드.
- SHA-1, SHA-256, SHA-512.
- 6자리 또는 8자리 코드.
- TOTP 주기, Unix time, HOTP counter 조정.
- Base32 secret 디코딩과 counter/dynamic truncation 상세 표시.

## 사용 방법

1. [TOTP / HOTP Simulator](../tools/DH.DevUtil.totp-hotp.html)를 엽니다.
2. 모드, hash, 자릿수, secret을 선택합니다.
3. 생성된 코드와 시간 또는 counter를 바꾸며 rollover 동작을 확인합니다.

모든 값은 현재 브라우저 탭 안에서만 처리됩니다. 학습용 도구이므로 운영 secret은 입력하지 마세요.
