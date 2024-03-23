# http code

> 상태 코드.
> 1. 요청의 처리 상태를 요약해서 알려주는 기능.
> 2. 1xx (informational): 요청이 수신되어 현재 처리 중
> 3. 2xx (Successful): 요청이 정상적으로 처리됨
> 4. 3xx (Redirection): 요청을 완료하기 위해서는 추가적인 행동이 필요함. (주로 리다이렉트 시 활용)
> 5. 4xx (Client Error): 클라이언트의 요청이 무언가 잘못되었음.
> 6. 5xx (Server Error): 서버가 현재 정상적으로 응답할 수 없음.

> 2xx
> 1. 200 OK
> 2. 201 Created
> 3. 202 Accepted: 요청은 수락되었으나 아직 수행되지는 않았음. (배치 등)
> 4. 204 No Content: 요청은 성공적으로 수행되었으나 보낼 데이터가 없음. (단순한 성공 인식)

> 3xx
> 1. 300 Multiple Choice