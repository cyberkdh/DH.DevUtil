# URL / Query Parser

[English](./URL_QUERY_PARSER.md)

URL을 외부로 보내지 않고 구성 요소와 query parameter를 검사·수정합니다.

## 기능

- protocol, username, host, port, pathname, hash, origin 검사.
- query parameter 추가·수정·삭제.
- `URLSearchParams`를 사용한 반복 parameter와 percent-encoding 처리.
- 다시 만든 URL 복사.

[URL / Query Parser](../tools/DH.DevUtil.url-query.html)를 열고 URL을 붙여 넣으세요. 주소창 외부에서 상대 URL을 처리하려면 base URL이 필요합니다.
