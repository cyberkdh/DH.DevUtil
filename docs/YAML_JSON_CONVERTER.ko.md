# YAML · JSON Converter

[English](./YAML_JSON_CONVERTER.md)

YAML · JSON Converter는 독립 실행형 HTML에서 일반적인 설정용 YAML과 JSON을 로컬로 변환합니다.

## 기능

- Mapping, sequence, 중첩 값, scalar 값, 일반적인 inline JSON 형식 값 변환
- 형식화된 JSON을 읽기 쉬운 YAML로 변환
- 설정, 서비스 목록, 중첩 데이터 샘플 제공
- 변환 전 선택한 샘플 원본 표시
- 입력·출력 방향 교체, 초기화, 결과 복사
- English·한국어 UI 전환

## 중요 사항

- YAML parser는 일반적인 설정 파일을 위한 작은 학습용 parser이며 완전한 YAML 1.2 구현이 아닙니다.
- Anchor, alias, custom tag, multi-document stream, complex key, 모든 block scalar 규칙을 지원하지 않습니다.
- 임의의 YAML 문서와 정확한 호환성이 필요하면 완전한 YAML library를 사용하세요.

## 개인정보 보호

모든 처리는 현재 브라우저 탭에서 이루어집니다. 값을 외부로 전송하거나 저장하지 않습니다.
