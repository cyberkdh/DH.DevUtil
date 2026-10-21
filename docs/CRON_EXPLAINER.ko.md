# Cron Explainer

[English](./CRON_EXPLAINER.md)

일반적인 5-field Unix cron 표현식을 설명하고 앞으로 실행될 local time을 계산합니다.

## 기능

- minute, hour, day-of-month, month, day-of-week 필드.
- wildcard, list, range, step 값.
- 사람이 읽기 쉬운 필드 설명과 다음 8개 실행 시각.
- 브라우저 내부 처리.

[Cron Explainer](../tools/DH.DevUtil.cron.html)를 엽니다. `L`, `W`, `#`, seconds, Quartz 문법 같은 확장은 해석하지 않고 일반 Unix cron 문법에 집중합니다.
