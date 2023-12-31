## 📝 Interview

#### HTTP는?
```
텍스트 기반의 통신 규약으로 서버-클라이언트 구조를 따르며 인터넷 상에서 데이터를 주고받는데 사용하는 프로토콜입니다.
```
<br>

#### HTTP의 상태코드가 무엇인지 그리고 대표적인 상태 코드에 대해 설명해주세요.
```
클라이언트가 보낸 요청의 처리상태를 응답에서 숫자로 표현하여 알려주는 기능입니다. 보통 100~500 사이의 숫자로 표현됩니다.
100번대는 요청을 수신하여 처리중임을 의미합니다.
200번대는 요청을 정상 처리했음을 의미합니다.
300번대는 요청을 완료하려면 추가행동이 필요함을 의미합니다.
400번대는 클라이언트쪽의 오류로 잘못된 문법등으로 서버가 요청을 처리할 수 없는 상태임을 의미합니다.
500번대는 서버 오류로 서버가 정상요청을 처리하지 못했음을 의미합니다.
```
<br>

#### HTTP 의 특징은?
```
HTTP는 TCP/IP 위에서 동작하는 프로토콜입니다. 서버와 클라이언트의 연결을 유지하지 않는 비연결성 프로토콜이며 서버가 클라이언트의 상태를 유지하지 않는 무상태 프로토콜입니다. 또한 클라이언트와 서버의 요청과 응답 구조로 HTTP 메시지를 이용해 통신하는 특징을 가지고 있습니다.
```
<br>

#### HTTP의 버전별 차이에 대해 설명해주세요.
```
```

<br>

#### HTTP 메서드에 대해 아는대로 설명해보시오.
```
HTTP 메서드는 클라이언트가 서버에게 사용자의 요청의 목적이나 종류를 알리는 수단입니다. 대표적으로 GET, POST, PUT, PATCH, DELETE가 있습니다. GET 메서드는 리소스 조회, POST 메서드는 요청 리소스 처리 및 리소스 등록, PUT은 리소스 대체, PATCH는 리소스 수정, DELETE는 리소스 삭제시 사용합니다.
```

<br>

#### HTTPS와 HTTP의 차이점은 무엇인가요
```
HTTP와 HTTPS의 차이점은 데이터의 암호화 입니다. HTTP는 전송 데이터가 암호화되지 않는 단점을 가지고있습니다. 이를 보완하기 위해 통신 보안을 제공하는 SSL을 사용해 클라이언트와 서버가 전송 데이터를 암호화하여 안전하게 사용할 수 있도록 만들어진 프로토콜 입니다.
```

<br>

#### HTTP와 Socket 통신방식의 차이점에 대해 설명해주세요.
```
HTTP는 기본적으로 비연결성의 특징을 가지고 있습니다. 클라이언트의 요청이 있을때에만 서버가 응답해서 데이터를 전송하고 곧바로 연결을 끊는 방식입니다. 즉, 클라이언트가 요청하고 서버가 응답하는 단방향 통신입니다.
이에 반해, socket 통신은 클라이언트와 서버가 특정 port를 통해 연결을 성립하고 있어 실시간으로 양방향 통신을 하는 통신 방식입니다. 클라이언트가 서버에게 요청을 보내는 http 통신과 달리 server도 client에게 요청을 보낼 수 있습니다. 따라서, 스트리밍이나 실시간 채팅등에 자주 사용됩니다.
```

<br>

#### SSL이란?
```
SSL이란 서버와 클라이언트 사이에 암호화된 연결을 만들어 안전한 데이터 교환이 가능하도록 하는 컴퓨터 네트워크에 통신보안을 제공하기 위해 설계된 프로토콜입니다. SSL은 보안과 성능상의 이유로 대칭키와 공개키 두가지 암호화 기법을 혼용해서 사용하며 SSL Handshake라는 과정을 통해 데이터 전송 전 보안 세션을 생성합니다.
```

<br>

#### SSL의 연결과정인 SSL Handshake에 대해 설명해주세요.
```
SSL Handshake 과정은 여덟단계를 통해 연결과정을 진행합니다.

먼저,

첫 번째로, ClinetHello 단계에서 사용자가 서버에 접속을 요청하며 Cipher Suite를 전달합니다.
두번째로, ServerHello 단계에서 서버는 클라이언트에게 전달받은 Cipher Suite중에서 서버가 사용가능한 암호화방식을 선택해 사용자에게 전달합니다.
세번째로, Certificate 단계에서 서버는 자신의 인증서를 사용자에게 전달합니다.
네번째로 ServerHelloDone 단계에서 사용자는 브라우저에 내장된 CA의 공개키를 이용해 사이트 인증서를 복호화하면서 인증서가 유효한지 검증하고 사이트의 공개키를 가져옵니다.
다섯번째로, ClientKeyExchange 단계에서 사용자는 자신이 전달할 데이터를 암호화할 대칭키를 만들고 그 대칭키를 사이트 공개키로 암호화합니다.
여섯번째로 사용자의 Finished 단계에서 암호화한 사용자의 대칭키를 서버에 전달합니다.
일곱번째로 서버 Finished 단계에서 사이트는 자신의 개인키를 사용하여 사용자 대칭키를 복호화하여 사용자의 대칭키를 얻습니다.
마지막으로 이렇게 얻은 대칭키를 활용하여 데이터를 암호화 및 복호화하며 통신합니다.
```

<br>
