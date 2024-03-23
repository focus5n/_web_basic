# HTTP Method

> PUT, PATCH 차이점
> 1. PUT 요청 시, 기존 정보를 삭제하고 요청한 정보를 넣는다.
> 2. PATCH 요청 시, 기존 정보 중 동일한 식별자가 있다면 수정하고, 없다면 기존 정보는 건드리지 않고 데이터를 추가한다.
> 3. PATCH 지원하지 않는 서버에는 POST 사용한다.

> HTTP Method 속성
> 1. Safe: 호출해도 리소스가 변경되지 않는다.
> 2. Idempotent (멱등): 몇 번을 호출해도 결과가 동일하다. f(f(x)) = f(x)
>   1. GET, PUT, DELETE
>   2. PUT 여러 번 호출하면 여러 번 동작하므로 멱등하지 않다.
>   3. 자동 복구 매커니즘에 활용.
>   4. 서버 문제로 (TIMEOUT etc) 정상 응답을 못 했다면, 클라이언트가 동일 요청을 해도 되는가? 판단의 근거.
>   5. 외부 요인으로 리소스가 변경되는 것을 고려하지 않는다. (멱등하지는 않다는 것을 서버에서 체크해야 한다.)
> 3. 일반적으로 GET 방식만 Caching 허용한다.

> 정적 데이터 조회 방식
> 1. 이미지 및 정적 텍스트 문서 조회
> 2. 위와 같은 경우는 GET 방식 사용
> 3. 쿼리 파라미터 없이 리소스 경로로 제공 가능

> Form 데이터로 요청 받음
> 1. form action method="post" 방식으로 요청을 하면, application/x-www-form-urlencoded 형식으로 요청이 들어온다.
> 2. 메시지 바디에 파라미터를 넣는데 형식은 key1=value1&key2=value2 방식이다.
> 3. form action method="get" 방식으로 요청을 넣는다.
> 4. 메시지 바디에 들어갈 내용을 쿼리 파라미터에 넣는다.
> 5. form action method="post" enctype="multipart/form-data" 파일 전송 양식
> 6. multipart/form-data 형식으로 넘어간다.
> 7. 주로 바이너리 데이터를 넘길 때 사용한다.

> HTTP API 데이터 전송이란?
> 1. HTTP 사용하여 서버로 바로 데이터를 전송하는 것을 HTTP API 데이터 전송이라고 부른다.
> 2. 서버 TO 서버 (백엔드 시스템 통신)
> 3. 앱 클라이언트 (아이폰, 안드로이드)
> 4. 웹 클라이언트 (ajax, react, vue.js)
> 5. POST, PUT, PATCH 방식처럼 메시지 바디를 통해 데이터 전송
> 6. GET 방식처럼 쿼리 파라미터 및 단순 조회를 위해 데이터 전달
> 7. application/json 사실상 표준


> API 정의서를 만들어야 한다면?

> 방식 1
> 1. 회원 목록 -> /members      => GET
> 2. 회원 조회 -> /members/{id} => GET
> 3. 회원 등록 -> /members      => POST
> 4. 회원 수정 -> /members/{id} => PATCH*(대부분 상황), PUT(게시글 수정), POST
> 5. 회원 삭제 -> /members/{id} => DELETE

> 방식 2
> 1. 파일 목록     -> /files            => GET
> 2. 파일 조회     -> /files/{filename} => GET
> 3. 파일 등록     -> /files/{filename} => PUT* (없으면 만들고, 있으면 덮어쓴다.)
> 4. 파일 대량 등록 -> /files            => POST
> 5. 파일 삭제     -> /files/{filename} => DELETE

> 방식 3
> 1. 회원 목록    -> /members              => GET
> 2. 회원 등록 폼 -> /members/new          => GET 
> 3. 회원 등록    -> /members/new, /members => POST
> 4. 회원 조회    -> /members/{id}          => GET
> 5. 회원 수정 폼 -> /members/{id}/edit     => GET
> 6. 회원 수정    -> /members/{id}/edit, /members/{id} => POST
> 7. 회원 삭제    -> /members/{id}/delete   => POST
> 8. /new, /edit, /delete 같은 컨트롤 URI 활용하여 PUT, PATCH, DELETE 대체하고 POST 방식도 명시

> 좋은 URI 설계 개념
> 1. 문서 (document)
>    1. 단일 개념 (파일 하나, 객체 인스턴스, 데이터베이스 ROW)
>    2. /members/100, /files/star.jpg
> 2. 컬렉션 (collection)
>    1. 서버가 리소스 URI 생성하고 관리
> 3. 저장소 (store)
>    1. 클라이언트가 리소스 URI 알고 관리
> 4. Control URI (Controller)
>    1. 문서, 컬렉션, 저장소 등으로 해결하기 어려운 추가 프로세스를 실행
>    2. 동사를 지정한다
>    3. /new, /edit, /delete => /members/134323/delete, /files/234dgvsdfdsf.jpg/upgrade

> API URI 설계 (URI)
> 1. 중요한 것은 리소스 설계
> 2. 행위는 리소스가 아니다. 관리대상이 리소스다. (조회, 등록 등은 행위) (회원은 리소스)
> 3. 행위와 리소스를 분리하라.

> POST 기반, PUT 기반, HTML FORM 기반
> 1. POST 방식으로 무언가를 등록했다면, 서버는 그 리소스가 위치한 Location 정보를 제공해야 한다.
> 2. Collection: 서버가 관리하는 리소스 디렉토리. (회원 관리 시스템) (POST 기반)
> 3. Store: 클라이언트가 리소스의 URI 알고 관리한다. (파일 관리 시스템) (PUT 기반)
> 4. HTML FORM 방식은 GET, POST 방식으로만 해결해야 한다.