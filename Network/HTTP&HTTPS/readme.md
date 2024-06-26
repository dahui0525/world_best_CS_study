![image](https://github.com/dahui0525/world_best_CS_study/assets/80496853/8dfe16b1-4dab-4e37-9e16-8d277bfed337)

## HTTP
Hypertext Transfer Protocol

클라이언트와 서버 간 통신을 위한 프로토콜<br>
(= 서로 다른 시스템들 사이에서 통신을 주고받게 해주는 가장 기초적인 프로토콜)


### HTTP 프로토콜의 특징
- OSI 모델 7계층 중에서 애플리케이션 계층 프로토콜이다.
- HTTP는 여러 유형의 요청과 응답을 정의한다.(GET, PUT ...) 또한 서버는 숫자 코드 및 데이터 양식으로 다양한 유형의 HTTP 응답을 전송한다.(200, 400, 404 ...)
- 암호화되지 않은 텍스트로 데이터를 주고 받기 때문에 보안상 좋지 않다.

<br>

## HTTPS
Hypertext Transfer Protocol Secure

HTTP 프로토콜의 보안 문제점을 해결한 프로토콜

브라우저와 서버가 데이터를 주고받기 전 안전하고 암호화된 연결을 설정하고,<br>
브라우저와 서버가 민감한 정보를 주고받을 때, 이것의 도난을 막아준다.

### HTTPS 프로토콜의 특징
- HTTP 통신에 보안 소켓 계층(SSL)을 추가한 것으로, HTTP 요청 및 응답을 SSL/TLS 기술에 결합하였다.
- 독립된 인증기관(CA)에서 SSL/TLS 인증서를 얻어야 한다. HTTPS 웹 사이트는 신뢰를 구축하기 위해 데이터를 교환하기 전에 브라우저와 인증서를 공유한다. SSL 인증서는 암호화 정보도 포함하기 떄문에 스크램블된 데이터를 교환할 수 있다.

### HTTPS 프로토콜의 동작과정
1. 사용자가 HTTPS 웹 사이트에 접속
2. 브라우저는 서버의 SSL 인증서를 요청하여 사이트의 신뢰성 검증 시도
3. 서버는 퍼블릭 키가 포함된 SSL 인증서를 회신
4. 웹 사이트의 SSL 인증서는 서버의 아이덴티티를 증명한다. 
5. 브라우저에서 인증되면, 브라우저가 퍼블릭 키를 사용하여 비밀 세션 키가 포함된 메세지를 암호화하고 전송한다.
6. 웹 서버는 개인키를 사용하여 메세지를 해독하독 세션 키를 검색한다. 이후 세션키를 암호화하고 브라우저에 승인 메세지를 전송한다.
7. 이제 브라우저와 서버 모두 동일한 세션키를 사용해 메세지를 교환할 수 있다.

### HTTP/2, HTTP/3, HTTPS의 차이점
HTTP/2,3은 프로토콜의 데이터 전송 시스템 자체를 수정하여 효율성을 높인 것이다. 2는 텍스트 대신 바이너리 형태로 교환하며, 서버가 새 HTTP 요청을 기다리는 대신 클라이언트 캐시에 응답을 미리 전송할 수 있다.
3은 2를 더 발전시킨 것으로 실시간 스트리밍 및 기타 최신 데이터 전송 요구를 보다 효율적으로 지원한다.

HTTPS는 HTTP에서 보안 문제를 우선한 것으로, 최신 시스템에서는 SSL/TLS와 함께 HTTP/2를 HTTPS로 사용한다.

### HTTPS의 장점
1. 보안
2. 권위(검색엔진도 신뢰성의 이유로 HTTP보다 HTTPS 컨텐츠를 우선한다고 함.)
3. 성능 및 분석(로드 속도가 HTTP보다 빠르다. 분석 SW가 신뢰할 수 있는 트래픽 소스 식별을 위해 HTTPS의 활성화가 필요하다.)

<br>

## HTTP와 HTTPS의 차이점
| | HTTP | HTTPS |
| ----- | ----- | ----- |
|의미| Hypertext Transfer Protocol | Hypertext Transfer Protocol Secure|
|기본 프로토콜| HTTP/1과 HTTP/2는 TCP/IP를 사용하고, HTTP/3은 QUIC 프로토콜 사용 | HTTP 요청 및 응답을 추가로 암호화하기 위해 SSL/TLS와 함께 HTTP/2 사용 |
|기본 포트| 80 | 443 |
|용도| 이전의 텍스트 기반 웹 사이트 | 모든 최신 웹 사이트 |
|보안| 보안기능 X | 공개키 암호화에 SSL 인증서 사용 |
|장점| 인터넷을 통한 통신 지원 | 웹 사이트에 대한 권위, 신뢰성 및 검색엔진 순위 개선 |


<br>


## ❓ 면접질문
**Q. HTTP 프로토콜에 대해 설명해주세요.**
```
A. HTTP(Hyper Text Transfer Protocol)이란 데이터를 주고 받기 위한 프로토콜이며, 서버/클라이언트 모델을 따릅니다.HTTP는 상태 정보를 저장하지 않는 Stateless의 특징과 클라이언트의 요청에 맞는 응답을 보낸 후 연결을 끊는 Connectionless의 특징을 가지고 있습니다.

장점
통신간의 연결 상태 처리나 상태 정보를 관리할 필요가 없어 서버 디자인이 간단하다.
각각의 HTTP 요청에 독립적으로 응답만 보내주면 OK


단점
이전 통신의 정보를 모르기 때문에 매번 인증을 해줘야 한다.
이를 해결하기 위해 쿠키(cookie)나 세션(session)을 사용해서 데이터를 처리한다.
``` 

<br>

**Q. HTTP와 HTTPS의 차이점은 무엇인가요?**
```
A. HTTP는 평문 데이터를 전송하는 프로토콜이기 때문에, HTTP로 중요한 정보를 주고 받으면 제 3자에 의해 조회될 수 있습니다. 이러한 문제를 해결하기 위해 HTTP에 암호화가 추가된 프로토콜이 HTTPS입니다.HTTPS는 SSL의 껍질을 덮어쓴 HTTP라고 할 수 있습니다.

※ SSL(Secure Socket Layer) 인터넷을 통해 전달되는 정보를 보호하기 위해 개발한 통신 규약

HTTP는 원래 TCP와 직접 통신했지만, HTTPS에서 HTTP는 SSL과 통신하고 SSL이 TCP와 통신함으로써 암호화와 증명서, 안전성 보호를 이용할 수 있게 됩니다.
```

