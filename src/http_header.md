# HTTP HEADER

```
1. HTTP 전송에 필요한 모든 부가정보 (MetaData)
2. General Header, ..., Message Body, Entity Header
3. Entity -> Representation
    - 표현 헤더   : 표현 데이터를 해석할 수 있는 정보 제공 (데이터 유형, 데이터 길이, 압축 정보 등)
    - 표현 헤더 구분 : 표현 메타데이터, 페이로드 메시지
    - 표현 데이터 : 실제 데이터
4. Message Body -> payload
```

> 표현
> 1. Content-Type
>    1. text/html, application/json, image/png ...
> 2. Content-Encoding
>    1. 표현 데이터 압축
>    2. 데이터를 읽는 쪽에서 해당 정보를 바탕으로 압축 해제
>    3. gzip, deflate, identity(압축 안함) ...
> 3. Content-Language
>    1. 표현 데이터의 자연 언어를 표현
>    2. ko, en, en-US ...
> 4. Content-Length
>    1. byte 단위
>    2. Transfer-Encoding 사용하면 Content-Length 사용하면 안됨.


> 협상
> 1. 클라이언트가 선호하는 표현으로 응답을 해달라는 요청
> 2. Accept
>    1. 클라이언트가 선호하는 미디어 타입 전달
> 3. Accept-Charset
>    1. 클라이언트가 선호하는 문자 인코딩
> 4. Accept-Encoding
>    1. 클라이언트가 선호하는 압축 인코딩
> 5. Accept-Language
>    1. 클라이언트가 선호하는 자연 언어
> 6. 요청 시에만 사용

> 협상 우선순위
> 1. Quality Values(q) 값 사용
> 2. 0 ~ 1, 클수록 우선순위 높음
> 3. 생략하면 1
> 4. Accept-Language: ko-KR,ko;q=0.9,en-US;q=0.8,en;q=0.7


> 전송 방식
> 1. 단순 전송
> 2. 압축 전송
> 3. 분할 전송, Content-Length 표현 금지
> 4. 범위 전송


> 일반 정보
> 1. From: 유저 에이전트의 이메일 정보
> 2. Referer: 현재 요청된 웹페이지의 이전 페이지 주소
> 3. User_agent: 클라이언트 애플리케이션 정보 (웹 브라우저 정보 등) -> 통계 정보
> 4. Server: ORIGIN 서버의 정보


> 특별 정보
> 1. Host: 요청한 호스트의 정보(Domain)
> 2. Allow: 405에서 응답에 포함해야 함.


> 인증
> 1. Authorization : 클라이언트 인증 정보를 서버에 전달
> 2. WWW-Authenticate : 리소스 접근 시 필요한 인증 방법 정의


> 쿠키
> 1. Set-Cookie : 서버에서 클라이언트로 쿠키 전달 (응답)
> 2. Cookie : 클라이언트가 서버에서 받은 쿠키를 저장하고, HTTP 요청 시 서버로 전달