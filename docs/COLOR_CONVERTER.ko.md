# Color Converter

[English](./COLOR_CONVERTER.md)

Color Converter는 색상 형식을 변환하고 WCAG 대비율을 계산하며 RGB·HSL·HSV·OKLCH 색상 공간의 차이를 학습하는 도구입니다.

## 기능

- `#RGB`, `#RGBA`, `#RRGGBB`, `#RRGGBBAA`를 RGB, HSL, HSV, OKLCH로 변환
- HEX와 CSS 결과에 alpha 유지
- 전경색·배경색의 WCAG 2 AA·AAA 대비 기준 확인
- 데스크톱에서 WCAG 입력·결과는 왼쪽, 실제 UI 미리보기는 오른쪽에 배치하고 작은 글자·본문·큰 글자·제목과 링크·버튼·입력창을 함께 표시
- English·한국어 UI와 학습 가이드 전환
- 독립 실행형 HTML에서 모든 값을 로컬 처리

## 사용 방법

1. 최신 브라우저에서 [Color Converter](../tools/DH.DevUtil.color-converter.html)를 엽니다.
2. HEX 색상을 입력하거나 color picker를 사용합니다.
3. 변환된 색상 형식과 OKLCH 값을 확인합니다.
4. 전경색과 배경색을 입력해 대비율을 확인합니다.
5. **전경색에 적용**, **배경색에 적용**, **전경색·배경색 교체** 버튼으로 위에서 선택한 색상을 WCAG 검사에 재사용할 수 있습니다.
6. **최적 대조색 추천**에서 목표 대비율을 선택하고 흑백 중 최적 색상, 중립 회색, Hue 유지 추천을 비교한 뒤 전경색·배경색에 적용할 수 있습니다.
7. 추천 컬러 팔레트에서 현재 Foreground·Background와 선택 색상 기반의 Primary, Surface, Dark, Canvas 조합을 함께 확인합니다. 각 팔레트 박스에는 실제 또는 추천 상대 색상도 함께 표시됩니다.

## 중요 사항

- RGB 채널은 0~255입니다. HSL은 색상·채도·명도를, HSV는 색상·채도·value를 사용합니다.
- OKLCH는 입력한 sRGB 색상에서 계산합니다. 지각 기반 색상 조정에 유용하지만 최종 sRGB 색상의 gamut clipping과 접근성은 별도로 확인해야 합니다.
- WCAG 대비율은 상대 휘도로 계산합니다. 일반 텍스트는 AA 4.5:1·AAA 7:1, 큰 텍스트는 AA 3:1·AAA 4.5:1이 필요합니다.
- 대비 미리보기는 입력 색상의 RGB 채널을 사용하며, 추가 배경에 대한 alpha 합성은 시뮬레이션하지 않습니다.
- Hue 유지 추천은 현재 Hue와 saturation을 최대한 유지하면서 HSL lightness를 조정하는 실용적인 제안이며, 색상 조화까지 보장하는 것은 아닙니다.
- 추천 팔레트는 디자인 시작점이며 브랜드 규칙이나 실제 제품의 색상 토큰을 자동으로 대체하지 않습니다.

## 개인정보 보호

모든 처리는 현재 브라우저 탭에서 이루어집니다. server endpoint, 외부 library, upload 기능, 입력값 영구 저장 기능이 없습니다. 선택한 UI 언어는 `localStorage`에 저장될 수 있습니다.
