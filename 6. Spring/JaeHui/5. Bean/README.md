# Bean

Bean이란 컨테이너 안에 들어있는 자바 객체를 의미합니다. <br>
컨테이너에 담겨있으며, 필요할 때 컨테이너에서 가져와서 사용하게 됩니다. <br>
`@Bean`을 사용하거나 xml 설정을 통해 일반 객체를 Bean으로 등록할 수 있고, Bean으로 등록된 객체는 쉽게 주입하여 사용 가능합니다. <br>

```
💡 Bean 생명 주기
스프링 컨테이너에 의해 생명주기가 관리되며 다음과 같은 순서로 진행됩니다.
1️⃣ 객체 생성: 스프링 컨테이너 초기화 시 빈 객체 생성
2️⃣ 의존 설정: 의존 객체 주입
3️⃣ 초기화
4️⃣ 사용
5️⃣ 소멸: 스프링 컨테이너 종료 시 빈 객체 소멸
```

## 초기화 및 소멸 방법 3가지

1️⃣ 사용 방법이 간결하며 코드에서 초기화 메소드가 존재함을 쉽게 파악 가능하여 xml 설정 방법보다 직관적입니다. (권장)<br>
초기화: 빈 초기화 메소드에 `@PostConstruct` 사용하여 xml에 `<context:annotation-config></context:annotation-config>` 추가<br>
소멸: 빈 소멸 메소드에 `@PreDestroy` 사용하여 xml에 `<context:annotation-config></context:annotation-config>` 추가<br>
<br>

2️⃣ 간결하지 않고 빈 코드에 스프링 인터페이스가 노출되어 권장하지 않는 방법입니다. (지양)<br>
초기화: `InitializingBean` 인터페이스의 `afterPropertiesSet()` 메소드 오버라이드<br>
소멸: DisposableBean 인터페이스의 destroy() 메소드 오버라이드<br><br>

3️⃣ 빈 코드에 스프링 인터페이스는 노출되지 않지만, 코드만으로 초기화 메소드 호출 여부를 알 수 없는 방법입니다. <br>
초기화: 커스텀 init() 메소드 정의<br>
xml에 init-method 속성으로 메소드 이름을 지정하거나, 빈 초기화 메소드에 `@Bean(init-method="init")`를 지정합니다.<br>
소멸 : 커스텀 destroy() 메소드 정의<br>
xml에 `destroy-method` 속성으로 메소드 이름 지정<br>

## [Bean Scope](https://gmlwjd9405.github.io/2018/11/10/spring-beans.html)

- singleton(default): Spring IoC 컨테이너 당 한 개의 인스턴스만 생성하는 것으로, 컨테이너가 Bean을 주입할 때 항상 같은 객체를 사용하여 메모리나 성능 최적화에 유리합니다.
- prototype: 컨테이너가 Bean을 주입할 때 항상 다른 인스턴스를 사용하여 모든 요청에서 새로운 객체가 생성됩니다. 안쓰는 객체는 GC에 의해 Bean이 제거됩니다.
- request: 하나의 HTTP Request 생명 주기 안에 단 하나의 Bean이 존재하는 것으로, 각 요청은 고유 Bean 각체를 보유합니다. Spring MVC Web Application에서 사용됩니다.
- session: 하나의 HTTP Session 안에 단 하나의 Bean이 존재하는 것으로, Spring MVC Web Application에서 사용됩니다.
- global session: 하나의 Global HTTP Session 생명주기 안에 하나의 Bean을 지정하는 것으로, Spring MVC Web Application에서 사용됩니다.
- application: 하나의 ServletContext 생명주기 안에 하나의 Bean이 존재하는 것으로, Spring MVC Web Application에서 사용됩니다.

```java
✅ @Bean 과 @Component의 차이

💡 @Bean
메소드 레벨에서 선언되며, 반환되는 객체(인스턴스)를 개발자가 수동으로 등록합니다.

💡 @Component
클래스 레벨에서 선언되며, 스프링이 런타임 시에 컴포넌트 스캔을 하여 자동으로 빈을 등록합니다.
```
