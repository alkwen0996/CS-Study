<details>
<summary><h3>📑목차</h3></summary>
<div markdown="1">

- [HTTP](#http)
- [HTTP/1.0](#http/1.0)
  - [RTT 증가 해결 방법](#rtt-증가-해결-방법)
    - [이미지 스플리팅 (이미지 스프라이트)](#이미지-스플리팅-(이미지-스프라이트))
    - [코드 압축](#코드-압축)
    - [이미지 Base64 인코딩](#이미지-base64-인코딩)
- [HTTP/1.1](#http/1.1)
- [HTTP/2](#http/2)
- [HTTPS](#https)
- [HTTP/3](#http/3)

</div>
</details>
<br>

# HTTP
`HTTP`(Hyper Text Transfer Protocol)는 클라이언트와 서버 간 정보를 주고받기 위한 통신 규약이다. 
`애플리케이션 계층`에서 동작하고 **웹 서비스 통신**에 사용된다. `HTTP/1.0`부터 `HTTP/3`까지 발전해왔다. 

## 📜HTTP/1.0
**한 연결당 하나의 요청을 처리**한다. 
서버로부터 정보를 가져올 때마다 TCP 연결(3-way handshake)과정이 필요하기 때문에 **RTT가 증가**한다는 단점이 있다.

> **RTT (Round Trip Time)** <br>
> -직역하면 "왕복 시간"이라는 의미<br>
> -인터넷 상에서 패킷이 송신지와 목적지 사이 왕복하는데 걸리는 시간을 말한다.<br>
> (패킷 왕복 시간)

<p align="center">
    <img src="./img/RTT.png" width="400">
      <br>
    <small>출처: 면접을 위한 CS 전공지식 노트</small>
</p>

<br>

### RTT 증가 해결 방법
매번 연결할 때마가 RTT가 증가하기 때문에 서버에 부담이 많이 가고 사용자 응답 시간이 길어진다.
이를 해결하기 위해 `이미지 스플리팅`, `코드 압축`, `이미지 Base64 인코딩`을 사용했다. 

#### 이미지 스플리팅 (이미지 스프라이트)
이미지 스프라이트라고도 불리는 이 기법은 **여러 개의 이미지를 하나의 이미지로 합쳐 관리**하는 것을 말한다.
합쳐 있는 하나의 이미지만 다운받고 이를 기반으로 필요한 이미지만 화면에 표시한다.
스프라이트 이미지에서 사용할 이미지의 정확한 `width`와 `height`, `position`값을 이용해 화면에 표시한다.

<p align="center">
    <img src="./img/sprite.png" width="600">
</p>

#### 코드 압축
코드에서 개행 문자, 빈칸을 없애 코드의 크기를 최소화하는 방법을 말한다. 

```
console.log('log1:'+txt);

if (true) {
  var txt = 'text';
  console.log('log2:'+txt);
}

console.log('log3:'+txt);
```

```
console.log('log1:'+txt);if(true){var txt='text';console.log('log2:'+txt)}console.log('log3:'+txt);
```


#### 이미지 Base64 인코딩
이미지 파일을 **64진법으로 이루어진 문자열로 인코딩**하는 방법이다. 
이미지가 Base64로 인코딩되어 있으면 해당 이미지 데이터는 **HTML 코드 내에 포함**되어 있다. 
따라서 서버에 이미지 파일을 따로 요청하여 파일로 저장할 필요가 없어지기 때문에 RTT를 줄일 수 있다. 
하지만 base64 문자열로 변환할 경우 약 33%의 크기가 더 커진다는 단점이 있다. 

<br>

## 📜HTTP/1.1
HTTP/1.0에서 발전된 형태로, **매번 TCP 연결을 하지않고** 
한 번 TCP 초기화 이후 `keep-alive` 옵션을 통해 여러 개의 파일을 송수신할 수 있다.
(keep-alive 표준화되어 기본 옵션으로 설정) 
아래 그림처럼 한번의 `TCP 3-way handshake`가 발생하면 그 다음부턴 발생하지 않는다. 

하지만 문서 안에 포함된 다수의 리소스를 처리하려면 요청 개수에 비례해 대기 시간이 길어진다는 단점(**HOL Blocking**)이 있다. 
또한, **헤더**에 쿠키 등 많은 메타데이터가 존재하고 압축되지 않아 **무겁다.**

<p align="center">
    <img src="./img/10vs11.png" width="500">
</p>

> **HOL Blocking(Head Of Line Blocking)** <br>
> 네트워크에서 같은 큐에 여러 패킷이 있을 때, 첫 번째 패킷의 지연시간이 길어져 발생하는 성능 저하 현상을 말한다.

<br>

## 📜HTTP/2
`HTTP/2`는 `HTTP/1.x`보다 지연 시간을 줄이고 응답 시간을 더 빠르게 할 수 있으며, 
`멀티플렉싱`, `헤더압축`, `서버푸시`, `요청의 우선순위 처리` 등을 지원한다.



