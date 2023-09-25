# Java SE vs EE

## Java SE(Standard Edition)

가장 보편적으로 쓰이는 자바 API Package로 Java Software Development Kit(SDK)로 구현됩니다. <br>
JDBC나 기본적인 기능이 모두 포함되어 있기 때문에 Android 개발 시 주로 사용합니다. <br>

## Java EE(Enterprise Edition)

Java SE 스펙 기반으로 자바를 이용한 서버측 개발을 위한 플랫폼으로, 엔터프라이즈 환경을 위한 도구입니다. <br>
EJB, JSP, Servlet, JNDI 등을 지원하며 애플리케이션 개발에 주로 사용됩니다. <br>

```

💡 EJB(Enterprise JavaBeans)
기업 환경의 시스템을 구현하기 위한 서버측 컴포넌트 모델로, 애플리케이션의 업무 로직을 가지고 있는 서버 애플리케이션이빈다.
Java EE의 API 중 하나로, 주로 웹 시스템에서 JSP는 화면 로직, EJB는 업무 로직을 처리하는 역할을 합니다.

```

<img src="./img/java se ee.jpeg" width="500"><br>

## Java ME(Micro Edition)

자바 마이크로 에디션은 제한된 자원을 가진 휴대폰, PDA, 셋탑박스 등에서 Java프로그래밍 언어를 지원하기 위해 만들어진 플랫폼입니다. <br>
임베디드 시스템에서 자바로 프로그램을 개발할 떄 이용합니다.<br>

#### Java FX

경량 사용자 인터페이스 API를 사용하여 리치 인터넷 어플리케이션을 만들 때 사용됩니다. <br>
JavaFX 어플리케이션은 하드웨어 수준에서 가속기능을 사용할 수 있는 그래픽과 미디어 엔진을 갖추고 있어, 클라이언트의 성능에 신경을 써야하는 분야에서 사용하면 좋습니다. <br>
JavaFX 어플리케이션 또한 자바 EE 플랫폼 서비스의 클라이언트 역할을 담당할 수 있습니다. <br>
