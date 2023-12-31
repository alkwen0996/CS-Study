## 📝 Interview

#### OSI 7계층과 TCP/IP 4계층의 차이점에 대해 설명하세요.

```
OSI 계층은 애플리케이션 계층을 애플리케이션, 프레젠테이션, 세션 계층, 총 3개의 계층으로 나누고,
링크 계층을 데이터 링크 계층, 물리 계층으로 나눠서 설명하는 것이 다르며,
인터넷 계층을 네트워크 계층으로 부른다는 점이 다릅니다.
```

<br>

#### TCP 연결 성립 과정에 대해 설명하세요.

```
3-way handshake 과정으로,
1. SYN 단계: 클라이언트는 서버에 클라이언트의 ISN을 담아 SYN을 보냅니다. ISN은 새로운 TCP 연결의 첫 번째 패킷에 할당된 임의의 시퀀스 번호를 말하며 이는 장치마다 다를 수 있습니다.
2. SYN + ACK 단계: 서버는 클라이언트의 SYN를 수신하고 서버의 ISN을 보내며 승인번호로 클라이언트의 ISN + 1을 보냅니다.
3. ACK 단계: 클라이언트는 서버의 ISN + 1한 값인 승인번호를 담아 ACK를 서버에 보냅니다.
```

<br>

#### TCP 연결 해제 과정에 대해 설명하세요.

```
4-way handshake 과정으로,
1. 클라이언트가 연결을 닫으려고 할 때 FIN으로 설정된 세그먼트를 보냅니다. 그리고 FIN_WAIT_1 상태로 들어가고 서버의 응답을 기다립니다.
2. 서버는 클라이언트로 ACK라는 승인 세그먼트를 보냅니다. 그리고 CLOSE_WAIT 상태에 들어갑니다. 클라이언트가 세그먼트를 받으면 FIN_WAIT_2 상태에 들어갑니다.
3. 서버는 ACK를 보내고 일정 시간 이후에 클라이언트에 FIN이라는 세그먼트를 보냅니다.
4. 클라이언트는 TIME_WAIT 상태가 되고 다시 서버로 ACK를 보내서 서버는 CLOSED 상태가 됩니다. 이후 클라이언트는 어느 정도의 시간을 대기한 후 연결이 닫히고 클라이언트와 서버의 모든 자원의 연결이 해제됩니다.
```

<br>

#### 캡슐화와 비캡슐화에 대해 설명하세요.

```
캡슐화란 상위 계층의 헤더와 데이터를 하위 계층의 데이터 부분에 포함시키고 해당 계층의 헤더를 삽입하는 과정을 말합니다.
애플리케이션 계층의 데이터가 전송 계층으로 전달되면서 세그먼트 또는 데이터그램화되며 TCP(L4) 헤더가 붙여지게 됩니다.
인터넷 계층으로 가면서 IP(L3) 헤더가 붙여지게 되며 패킷화가 되고, 이후 링크 계층으로 전달되면서 프레임 헤더와 프레임 트레일러가 붙어 프레임화가 됩니다.

비캡슐화란 하위 계층에서 상위 계층으로 가며 각 계층의 헤더 부분을 제거하는 과정을 말합니다.
이렇게 캡슐화된 데이터를 받게 되면 링크 계층에서부터 타고 올라오면서 프레임화된 데이터는 다시 패킷화를 거치고
세그먼트, 데이터그램화를 거쳐 메시지화가 되는 비캡슐화 과정이 일어납니다.
그 이후 최종적으로 사용자에게 애플리케이션의 PDU인 메시지로 전달됩니다.
```

<br>

#### TCP/IP 4계층별 PDU에 대해 설명하세요.

```
네트워크의 어떤한 계층에서 계층으로 데이터가 전달될 때 한 덩어리의 단위를 PDU라고 합니다.
제어 관련 정보들이 포함된 헤더, 데이터를 의미하는 페이로드로 구성되어 있으며 계층마다 부르는 명칭이 다릅니다.
- 애플리케이션 계층: 메시지
- 전송 계층: 세그먼트(TCP), 데이터그램(UDP)
- 인터넷 계층: 패킷
- 링크 계층: 프레임(데이터 링크 계층), 비트(물리 계층)
```
