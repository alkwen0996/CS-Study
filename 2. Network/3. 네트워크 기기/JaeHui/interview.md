## 📝 Interview

#### L4 스위치와 L7 스위치의 차이에 대해 설명하세요.

```
L4 스위치는 전송 계층을 처리하는 기기로 스트리밍 관련 서비스에서는 사용할 수 없으며 메시지를 기반으로 인식하지 못하고 IP와 포트를 기반으로 트래픽을 분산합니다.
L7 로드밸런서는 IP, 포트 외에도 URL, HTTP 헤더, 쿠기 등을 기반으로 트래픽을 분산합니다.
클라우드 서비스(AWS 등)에서 L7 스위치를 이용한 로드밸런싱은 ALB(Application Load Balancer) 컴포넌트로 하며, L4 스위치를 이용한 로드밸런싱은 NLB(Network Load Balancer) 컴포넌트로 합니다.
```

<br>

#### 로드밸런서의 역할에 대해 설명하세요.

```
서비스를 안정적으로 운용하기 위해서는 에러 발생에도 서비스가 정상적으로 운용되어야 하기 때문에 2대 이상의 서버는 필수적입니다.
로드밸런서는 2대 이상의 서버를 기반으로 가상 IP를 제공하고 이를 기반으로 안정적인 서비스를 제공합니다.
```
