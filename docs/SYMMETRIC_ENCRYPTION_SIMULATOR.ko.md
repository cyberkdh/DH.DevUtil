# Symmetric Encryption Simulator

[English](./SYMMETRIC_ENCRYPTION_SIMULATOR.md)

Symmetric Encryption Simulator는 대칭키 암호의 암호화와 복호화 흐름을 로컬 브라우저에서 비교하는 학습 도구입니다. AES-GCM, AES-CBC, AES-CTR 및 AES-CBC의 padding 옵션을 제공합니다.

기초부터 보려면(양쪽이 같은 키와 IV를 쓰는 이유, ECB와 CBC 비교, padding, ARIA/3DES/DES, 고정 IV) [Symmetric Encryption Simulator (Base)](./SYMMETRIC_ENCRYPTION_SIMULATOR_BASE.ko.md)를 참고하세요.

## 화면 미리보기

![Symmetric Encryption Simulator 화면 미리보기](./images/DH.DevUtil.symmetric-encryption-simulator.png)

이미지에는 도구 화면 설명을 위한 테스트 문자열과 임시 키가 포함되어 있습니다. 실제 운영 키나 개인정보를 입력하지 마세요.

## 기능

- AES key 128/192/256-bit 무작위 생성. 현재 Web Crypto 구현에서 AES-GCM/CTR은 128/256-bit를 사용하고 AES-CBC는 128/192/256-bit를 지원
- AES-GCM 인증 암호화(AEAD): 96-bit nonce, 선택적 Additional Authenticated Data (AAD), 변조 시 인증 실패
- AES-CBC: PKCS#7, ANSI X.923, Zero, NoPadding 선택
- AES-CTR: 128-bit counter block과 64-bit 증가 counter 사용
- package JSON에 암호 알고리즘, IV/nonce 또는 counter, ciphertext 등 저장. secret key는 package에 포함하지 않음
- package와 올바른 key로 복호화하고 모드별 계산 상세 표시
- DES·3DES의 legacy 상태와 ARIA의 미지원 사유 안내
- 처리와 키 생성은 브라우저 안에서 수행. 네트워크 전송이나 영구 저장 없음

## 사용 방법

1. 최신 브라우저에서 [Symmetric Encryption Simulator](../tools/DH.DevUtil.symmetric-encryption-simulator.html)를 엽니다. HTML 파일 하나만으로 동작합니다.
2. AES mode와 key size를 선택하고 **Generate key**를 눌러 임시 key를 만듭니다. 필요하면 합성(synthetic) 테스트 문장을 입력합니다.
3. AES-CBC 선택 시 padding 방식을 고릅니다. **No padding**은 UTF-8 바이트 길이가 16의 배수여야 합니다. AES-GCM과 AES-CTR에는 block padding이 적용되지 않습니다.
4. **Encrypt**를 누릅니다. 생성된 JSON package를 복사해 보관할 수 있습니다. 복호화하려면 package와 동일한 AES key가 필요합니다.
5. package를 다시 붙여 넣거나 편집하고 **Decrypt package**를 누릅니다.

## Mode와 padding의 의미

### AES-GCM

Galois/Counter Mode (GCM)는 암호화와 인증을 결합한 AEAD mode입니다. 12-byte nonce를 매번 무작위로 생성합니다. 동일한 key로 nonce를 재사용하면 심각한 보안 문제가 발생할 수 있으므로 production에서는 nonce 관리를 별도로 설계해야 합니다. AAD는 암호화되지는 않지만 ciphertext와 함께 인증됩니다.

### AES-CBC

Cipher Block Chaining (CBC)은 임의 길이의 plaintext에 block padding을 사용합니다. 이 도구는 다음 방식을 제공합니다.

- **PKCS#7**: padding byte 수와 같은 값으로 padding 영역을 채웁니다. 이미 블록 경계에 맞는 입력에도 16-byte block을 추가합니다.
- **ANSI X.923**: 마지막 byte에 padding 길이를 기록하고 그 앞의 padding bytes는 0으로 채웁니다. 블록 경계 입력에도 padding block을 추가합니다.
- **Zero padding**: 남은 영역을 0으로 채웁니다. 원본 끝에 있는 0과 padding을 구분할 수 없으므로 package의 `plaintextLength` 메타데이터를 사용합니다. 이 길이는 인증되지 않습니다.
- **NoPadding**: 입력의 UTF-8 byte 길이가 16의 배수일 때만 허용합니다.

CBC는 ciphertext 무결성이나 발신자 인증을 제공하지 않습니다. 패딩 오류 또는 복호화 결과가 있다고 해서 데이터가 진짜이거나 변경되지 않았다는 뜻은 아닙니다. production 설계에서는 GCM과 같은 AEAD를 우선 사용하세요.

### AES-CTR

Counter (CTR) mode는 임의 길이의 입력을 처리하므로 block padding이 없습니다. 128-bit 초기 counter block을 만들고 그중 64-bit를 counter 증가 영역으로 사용합니다. 동일 key에서 counter block을 재사용하면 안 됩니다. CTR만으로는 변조를 감지하지 못합니다.

## 구현과 지원 범위

- AES-GCM 및 AES-CTR은 브라우저 Web Crypto API를 사용합니다.
- AES-GCM/CTR의 192-bit key 지원 여부는 브라우저 구현에 따라 다릅니다. 현재 검수 환경은 이를 거부하므로 해당 mode에서는 192-bit 선택을 제한합니다. AES-CBC는 192-bit key도 지원합니다.
- Web Crypto의 AES-CBC는 항상 PKCS#7을 적용해 다른 padding을 선택할 수 없으므로, AES-CBC는 HTML 안에 순수 JavaScript로 구현한 AES를 사용합니다. NIST SP 800-38A 테스트 벡터와 OpenSSL로 결과를 검증했으며, 외부 라이브러리는 사용하지 않습니다.
- 가져오기/내보내기용 package는 학습용 version 1 JSON 형식이며, 각 mode에 필요한 IV/counter, padding(해당 시), ciphertext 정보를 포함합니다. 형식은 학습용이며 표준 암호 컨테이너 포맷이 아닙니다.
- ARIA는 이 브라우저/Web Crypto 기반 버전에서 구현하지 않으며, [Symmetric Encryption Simulator (Base)](./SYMMETRIC_ENCRYPTION_SIMULATOR_BASE.ko.md)에서 학습할 수 있습니다. DES와 3DES/TDEA도 신규 암호화에 적합하지 않은 legacy cipher이므로 실행 가능한 선택지에 포함하지 않습니다.
- ECB mode는 반복 plaintext pattern을 드러내므로 지원하지 않습니다.

## 보안 안내

**운영 key, 개인정보, 실제 민감 plaintext를 넣지 마세요.** AES-CBC와 AES-CTR은 인증을 제공하지 않습니다. Zero padding의 길이 메타데이터와 CBC/CTR package도 변조 방지되지 않습니다. 도구는 강의용 예제이지 보안 저장이나 production encryption 대체물이 아닙니다.
