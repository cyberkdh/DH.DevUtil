# Timestamp Converter

[English](./TIMESTAMP_CONVERTER.md)

Timestamp Converter는 브라우저에서 개발에 자주 사용하는 시간 형식을 변환하고, 년·개월·일·시간·분·초를 날짜에 더하거나 빼는 도구입니다.

## 화면 미리보기

![Timestamp Converter 화면 미리보기](./images/DH.DevUtil.timestamp-converter.png)

## 기능

- ISO 8601과 브라우저 날짜 문자열 변환
- Unix 초·밀리초·마이크로초·나노초 변환
- Windows FILETIME 변환(1601-01-01부터 100나노초 단위)
- .NET Ticks 변환(0001-01-01부터 100나노초 단위)
- 값의 크기를 기준으로 Unix 단위를 자동 감지
- UTC ISO 8601, local time, Unix 단위, FILETIME, .NET Ticks를 한 번에 표시
- 한국어 UI에서는 local date/time을 한국식 날짜와 오전·오후 형식으로 표시하며 ISO 결과는 표준 형식을 유지
- native `datetime-local` 컨트롤 자체의 표시 형식은 브라우저와 운영체제가 결정하므로, 아래에 선택한 값을 현재 UI 언어로 다시 표시
- 년·개월과 일·시간·분·초를 calendar arithmetic으로 더하거나 빼기
- 전체 UI와 Learn more의 English·한국어 전환
- 브라우저의 `Date`·`Intl` API로 모든 값을 로컬 처리

## 사용 방법

1. 최신 브라우저에서 [Timestamp Converter](../tools/DH.DevUtil.timestamp-converter.html)를 엽니다.
2. ISO 날짜 또는 숫자 timestamp를 입력합니다. 자동 감지가 적절하지 않으면 **해석 방법**을 선택합니다.
3. 변환 결과를 확인합니다. 각 행의 **복사** 버튼으로 값을 복사할 수 있습니다.
4. 날짜 계산은 기준 날짜·시간을 입력하고 **더하기 (+)** 또는 **빼기 (-)**를 선택한 뒤 기간을 입력합니다.
5. **현재 시간 사용** 또는 **예제 불러오기**로 빠르게 시작할 수 있습니다.

## 중요 사항

- Unix timestamp는 1970-01-01T00:00:00Z부터의 시간입니다.
- JavaScript `Date`는 밀리초를 저장하므로 1밀리초보다 작은 입력은 표시 날짜 계산에서 가장 가까운 밀리초로 처리됩니다.
- `Z`로 끝나는 ISO 값은 UTC입니다. offset이 없는 날짜·시간은 브라우저 local time으로 해석됩니다.
- 년과 월은 JavaScript calendar arithmetic으로 계산합니다. 1월 31일에 한 달을 더하면 3월로 overflow될 수 있으며, 고정된 일수를 더하는 것과 다릅니다.
- FILETIME과 .NET Ticks는 JavaScript safe integer 범위를 넘을 수 있습니다. 매우 큰 값은 `Number` 정밀도 손실이 생길 수 있습니다.

## 개인정보 보호

모든 처리는 현재 브라우저 tab에서 이루어집니다. server endpoint, 외부 library, upload 기능, 입력값 영구 저장 기능이 없습니다. 선택한 UI 언어는 `localStorage`에 저장될 수 있습니다.
