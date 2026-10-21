# PEM · ASN.1 · X.509 Viewer

[English](./PEM_ASN1_X509_VIEWER.md)

`.pem`, `.crt`, `.cer`, `.der` 파일을 파일 선택 버튼, drop zone, editor 직접 drag-and-drop으로 불러올 수 있습니다. 버튼 hover와 focus 상태의 대비도 보강했습니다.

JKS 파일은 certificate chain의 첫 번째 인증서를 추출하고, PFX/P12 파일은 외부 PKCS#12 ASN.1 구조를 표시합니다. JKS private key는 표시하지 않으며 PFX/P12의 암호화된 safe contents는 복호화하지 않습니다.

PEM · ASN.1 · X.509 Viewer는 PEM 또는 DER 16진수 입력을 로컬에서 디코딩하고 ASN.1 트리를 표시하며, 인증서 입력이면 주요 X.509 필드를 추출합니다.

## 기능

- PEM 텍스트 또는 DER 16진수 바이트 입력
- 중첩 ASN.1 tag, 길이, OID, 문자열, 바이트 미리보기 표시
- Serial, Issuer, Subject, Validity, 서명 알고리즘, 공개 키 알고리즘 추출
- 작은 ASN.1 구조 샘플, 검사, 초기화, 요약 복사
- English·한국어 UI 전환

## 중요 사항

- 내장 샘플은 서명된 운영 인증서가 아니라 작은 ASN.1 DER 구조입니다.
- 로컬 구조 뷰어·학습용 검사 도구이며 인증서 chain, trust, revocation, hostname, signature를 완전히 검증하지 않습니다.
- PEM label은 Base64 DER 바이트로 디코딩할 뿐이며 문법적으로 유효하다고 인증서를 신뢰하지 않습니다.

## 개인정보 보호

모든 처리는 현재 브라우저 탭에서 이루어집니다. 인증서를 외부로 전송하거나 저장하지 않습니다.
