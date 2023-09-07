## 스프링 프레임워크 ( Spring Framework )

---

### Spring 이란?

`Spring` 이란 `Spring Framework` 를 기반으로 `Spring Boot`등 `Spring` 의 여러 서브 프로젝트의 모음으로 이루어져 있으며 서브 프로젝트들은 각각 여러 모듈을 가지고 있다. 그래서 개발할 애플리케이션에 맞게 적합한 여러 모듈을 조합해서 사용할 수 있다. `Spring` 의 프로젝트들은 `Spring Framework` 기반으로 동작한다. 따라서, `Spring Framework` 는 `Spring` 의 가장 핵심이 되는 프로젝트라고 할 수 있다.

<br>

### Spring Framework 란?

`Spring Framework` 는 엔터프라이즈용 Java 기반 애플리케이션 개발을 위한 오픈소스 경량 애플리케이션 프레임 워크로 순수 자바 객체 ( POJO ) 만을 사용하여 복잡성을 제거하고 단순하고 가벼운 코드로 기업용 애플리케이션 개발하기 위한 목적으로 만들어졌다.

`Spring Framework` 는 `IoC`, `DI`, `AOP` 등의 핵심 기능을 통해 객체 지향의 특징을 잘 활용하여 애플리케이션을 개발할 수 있도록 하며 엔터프라이즈 기술을 처리하는 코드와 핵심 비즈니스 로직을 분리하여 개발자들이 핵심 비즈니스 로직 구현에 더 집중할 수 있도록 하는 프레임 워크이다.

<br>

### Spring Framework 특징

- 경량 컨테이너로서 자바 객체의 생명주기를 직접 관리
- POJO 방식의 프레임 워크
- IOC ( Inversion of Control, 제어의 역전 ) 지원
- DI ( Dependency Injection, 의존성 주입 ) 를 통한 객체 관계 구성 지원
- AOP ( Aspect-Oriented Programming, 관점 지향 프로그래밍 ) 지원
- 영속성 관련 API 지원

<br>

### Spring Boot 란?

`Spring Boot` 는 `Spring` 프로젝트 중 하나로, `Spring Framework`의 복잡한 설정을 간소화하여 보다 쉽고 빠르게 스프링 애플리케이션을 개발할 수 있도록 기능을 제공하는 도구이다.

<br>

### Spring Boot 주요 장점

**[ 내장 서버 ]**

`Spring Framework` 을 통해 개발한 웹 애플리케이션을 배포 하려면 별도의 `WAS` 가 필요하다. 애플리케이션을 `WAR` 파일로 패키징하고 별도의 `WAS` 파일을 설치한 후 `WAS`를 통해 `WAR` 파일을 실행시켜야 한다.

하지만, `Spring Boot` 는 `톰캣` 등 `WAS`를 내장하여 제공한다. 또한, 별도로 `WAR` 파일로 패키징 하여 외부 `WAS`로 실행할 수도 있지만 `Jar` 파일로 패키징 하여 바로 사용할 수 있다. 이를 통해 개발자들은 별도로 웹 서버를 설치할 필요 없고 `WAR` 파일로 패키징 할 필요 없이 독립적으로 빠르게 실행가능한 애플리케이션을 개발 할 수 있게 되었다.

**[ 의존성 및 권장 버전 관리 ]**

기존 `Spring Framework` 는 개발에 필요한 모듈의 의존성을 개발자가 직접 다운받아야 했으며 필요한 모듈의 버전을 개발자가 직접 명시해줘야 했다. 하지만, 모듈간 의존성이 존재하는 경우가 있고 버전간의 충돌이 발생하는 경우가 생기는 문제가 있었다.

이런 문제를 해결하기 위해 `Spring Boot` 는 `spring-boot-starter` 라는 패키지를 지원해준다. 해당 패키지는 자주 사용하게 되는 모듈간의 의존성과 버전 조합을 제공해준다. 따라서 패키지 하나의 의존성을 추가하면 관련한 라이브러리를 모두 가져와 사용할 수 있게 된다.

예를 들어, `gradle` 을 빌드 도구로 사용하는 경우 `web` 을 개발하고 싶다면 `Spring MVC`와 `내장 톰캣` 등을 제공하는 `‘org.springframework.boot:spring-boot-starter-web’` 패키지를 추가하면 된다.

또한, `Spring Boot` 는 의존성을 추가한 라이브러리의 버전 정보를 관리해 준다. 마찬가지로 `gradle` 을 빌드 도구로 사용하는 경우 `'io.spring.boot.dependency-management'` 플러그인을 추가하면 의존성을 추가한 라이브러리의 버전정보를 생략하고 작성이 가능하다.

**[ 자동 설정 ]**

일반적으로 자주 사용하는 수 많은 빈 들을 `Spring Boot` 에서 자동으로 등록해주는 기능이다. 기존에 `xml 파일` 또는 `Java 코드` 로 빈 등록 및 설정 코드들을 작성해야 했으나 `Spring Boot` 에서는 의존성 추가와 `yaml` 에 약간의 코드 만으로 간편하게 설정 할 수 있도록 `자동 설정` 기능을 제공한다.

필요한 의존성을 추가하면 `Spring Boot` 가 추가된 `Jar 파일` 을 인지하여 관련된 스프링 설정을 자동으로 처리한다. 이때 자동 설정 역할은 메인 클래스 위에 생기는 `@SpringBootApplication` 내부의 `@EnableAutoConfiguration` 이 담당한다. `@EnableAutoConfiguration` 내부의`@Import(AutoConfigurationImportSelector.class)` 에 있는 `selectImports()` 가 자동 설정할 빈을 결정해준다.

**[ 모니터링 ]**

`Spring Boot` 사용하면 `Spring Boot` 의 모듈 중 하나 인 `Actuator` 를 통해 실행중인 애플리케이션의 상태를 관리 및 모니터링 할 수 있다. `Actuator` 는 상용 서비스 수준에서 필요로 할 모니터링 기능을 엔드 포인트로 미리 만들어서 제공해준다. 이를 통해 실행중인 애플리케이션 내에서 애플리케이션의 상태 정보와 어떤 빈이 등록되어 있는지 자동 설정이 어떻게 되어 있는지 환경변수나 시스템 속성 등을 확인할 수 있다.

<br>

### [ Reference ]

[프레임워크(Framework)와 라이브러리(Library)의 차이점](https://www.devkuma.com/docs/framework-and-library/)

[Framework vs Library (feat. IoC, 왜 프레임워크를 써야할까?)](https://seongwon.dev/ETC/20220627-Framework-vs-Library/)

[[10분 테코톡] 🏀 에어의 Spring vs Spring Boot](https://www.youtube.com/watch?v=Y11h-NUmNXI)
