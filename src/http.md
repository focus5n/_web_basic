# http

> HTML 요청 메시지, 응답 메시지는 형식이 다르다.
> 
> start-line
> header
> empty line (공백 CRLF)
> message body
 
1. 요청 메시지 
2. start-line = request-line / status-line
3. request-line = method (공백) request-target (공백) HTTP-Version (엔터, CRLF)

4. 응답 메시지
5. start-line = request-line / status-line
6. status-line = HTTP-Version (SP) status-code (SP) reason-phrase (CRLF)
7. 200: 성공, 400: 요청 오류, 500: 서버 오류

8. HTTP Header
9. header-field = field-name ":" (OWS, 띄어쓰기 허용) field-value (OWS)
10. filed-name 대소문자 구문하지 않음