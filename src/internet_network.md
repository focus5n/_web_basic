# Internet Network

1. Client
2. Server
3. Node
4. Internet Protocol (IP)
   
## Internet Protocol

1. 지정한 IP 주소에 데이터를 전달
2. 데이터는 패킷이라는 통신 단위로 분할
3. 한계
   1. 패킷을 받을 대상이 받을 수 없는 상태여도 패킷을 전송하고, 이를 패킷을 보낸 사람이 알 방법이 없음
   2. 중간에 패킷이 사라질 수 있다.
   3. 패킷이 순서대로 도착하지 않을 수 있다.
   4. 같은 IP 주소에서 사용하는 애플리케이션이 둘 이상이면 어떻게 구분하는가?
4. 포트 정보가 없다.

## TCP/IP Suite

1. Application Layer
   1. HTTP, FTP
2. Transmission Layer
   1. TCP, UDP
3. Internet Layer
   1. IP
4. Network Interface Layer
   1. 랜카드, 네트워크 랜 드라이버

5. 연결을 유지하는 비용을 최소화할 수 있다.
6. Three-way handshake 비용이 계속 추가된다.
7. Persistence Connection (지속 연결)
8. 기본연결: 연결 -> HTML 요청 및 응답 -> 종료 => 연결 ->  JS 요청 및 응답 -> 종료 => 연결 -> 이미지 요청 및 응답 -> 종료
9. 지속연결: 연결 -> HTML 요청 및 응답 -> JS 요청 및 응답 -> 이미지 요청 및 응답 -> 종료

## 데이터 전송 과정

1. 프로그램에서 메시지 생성
2. Socket 라이브러리를 통해 전달
3. TCP 정보 생성, 메시지 데이터 포함
4. IP 패킷 생성, TCP 데이터 포함
5. 랜카드를 통해 인터넷 활용 (MAC 주소 활용)
6. 서버에 전달

## TCP Three-way Handshake

*. TCP 에는 PORT 정보가 있다.
1. SYN : 접속 요청
2. SYN + ACK : 접속 요청 + 요청 수락
3. ACK : 요청 수락 + 데이터 전송
4. 개념적 연결. 나를 위한 전용랜선이 보장되는 것은 아니므로 물리적 연결을 확신하는 것은 아니다.
   1. 중간 노드가 문제가 생길 수 있다.

## UDP

1. IP 비슷하지만 PORT 기능이 존재한다.
2. 별 다른 기능이 없다.
3. 반대로 기능을 원하는대로 추가하거나 최적화할 수 있다.
4. TCP 보다 더 빠른 속도를 기대할 수 있다.

## Port

1. 0 ~ 65535 할당 가능
2. 0 ~ 1023  잘 알려진 포트이므로 사용 자제
   1. FTP    - 20, 21
   2. TELNET - 23
   3. HTTP   - 80
   4. HTTPS  - 443

## Packet

1. 출발지 IP + Port
2. 도착지 IP + Port
3. 전송 데이터
4. etc...

## URI, Uniform Resource Identifier