# Spring Boot

## [Spring Boot](https://www.codestates.com/blog/content/%EC%8A%A4%ED%94%84%EB%A7%81-%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8)

스프링은 기존 기술의 복잡성을 크게 줄인 프레임워크지만, 그럼에도 불구하고 여러 가지의 사항들을 설정해주어야 합니다. <br>
Spring Boot는 이를 보완하기 위해 스프링으로 애플리케이션을 만들 때 필요한 설정을 간편하게 처리해주는 별도의 프레임워크입니다. <br>
설정 정보를 간략화할 수 있는 이유는 Spring Boot가 기존 복잡한 설정을 대신하고 있기 때문입니다. <br>
초기 설정에 쏟아야 하는 시간과 노력을 절약하여 개발자는 비즈니스 로직을 구현하는 데에 집중할 수 있습니다. <br><br>

또한 기존 배포 시 별도의 외장 웹 서버를 설치 후 프로젝트를 war 파일로 필드해야 해서 느리고 번거로웠습니다. <br>
Spring Boot는 자체적인 웹 서버를 내장하고 있어 빠르고 간편하게 배포를 진행할 수 있습니다. <br>
독립적으로 실행 가능한 jar 파일로 프로젝트를 빌드할 수 있어 클라우드 서비스 및 도커와 같은 가상화 환경에 빠르게 배포할 수 있습니다. <br><br>

Spring Framework와 달리 Spring Boot에는 AutoConfiguration이 있습니다. <br>
SpringBoot로 애플리케이션을 만들면 클래스에 @SpringBootApplication이라는 어노테이션을 확인할 수 있습니다. <br>
이 어노테이션 덕분에 많은 외부 라이브러리, 내장 톰캣 서버 등이 실행될 수 있습니다.<br>
이를 제거하고 실행하면 일반적인 자바 프로그램과 동일하게 실행됩니다. <br>

```java
💡 @SpringBootApplication 내부 들여다보기
@ComponentScan: @Component, @Controller, @Repository, @Service 어노테이션이 붙어있는 객체들을 스캔하여 자동으로 Bean에 등록해 줍니다.
@EnableAutoConfiguration: @ComponentScan 이후 사전에 정의한 라이브러리들을 Bean에 등록해줍니다.
```
