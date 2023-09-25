# [Annotation](https://velog.io/@gillog/Spring-Annotation-%EC%A0%95%EB%A6%AC)

Java5에 추가된 문법 요소로, 자바 코드에 @를 이용해 주석처럼 달아 특수한 의미를 부여하는 것입니다.<br>
프로그램 코드의 일부가 아닌 프로그램에 관한 데이터를 제공하고, 코드에 정보를 추가하는 정형화된 방법입니다. <br>
어노테이션을 사용하면 코드가 깔끔해지고 재사용 가능성을 높일 수 있습니다.<br>

- @ComponentScan: @Service, @Repository, @Controller, @Configuration이 붙은 클래스 Bean들을 찾아서 Context에 bean등록을 해주는 Annotation
- @Component: 개발자가 직접 작성한 Class를 Bean으로 등록하기 위한 Annotation
- @Bean: 개발자가 직접 제어가 불가능한 외부 라이브러리등을 Bean으로 만들려할 때 사용되는 Annotation
- @Autowired: 속성(field), setter method, constructor(생성자)에서 사용하며 Type에 따라 알아서 Bean을 주입해주는 것입니다.
- @Inject: @Autowired 어노테이션과 비슷한 역할
- @Controller: Spring의 Controller로 Spring MVC에서 Controller클래스에 쓰입니다.
- @RestController: Spring에서 Controller 중 View로 응답하지 않는, Controller를 의미합니다.

```java
✅ @Controller 와 @RestController 의 차이

💡 @Controller
API와 view를 동시에 사용하는 경우에 사용합니다.
대신 API 서비스로 사용하는 경우는 @ResponseBody를 사용하여 객체를 반환합니다.
view(화면) return이 주목적입니다.

💡 @RestController
view가 필요없는 API만 지원하는 서비스에서 사용합니다.
Spring 4.0.1부터 제공하며, @RequestMapping 메서드가 기본적으로 @ResponseBody 의미를 가정합니다.
data(json, xml 등) return이 주목적입니다.
즉, @RestController = @Controller + @ResponseBody 인 것입니다.
```

- @Service: Service Class에서 쓰이는 것으로, 비즈니스 로직을 수행하는 Class라는 것을 나타내는 용도입니다.
- @Repository: DAO class에서 쓰이며, DataBase에 접근하는 method를 가지고 있는 Class에서 쓰입니다.
- @CrossOrigin: CORS 보안상의 문제로 브라우저에서 리소스를 현재 origin에서 다른 곳으로의 AJAX요청을 방지하는 것입니다.
- @RequestBody: 요청이 온 데이터(JSON이나 XML형식)를 바로 Class나 model로 매핑하기 위한 Annotation입니다.
- @PathVariable: method parameter 앞에 사용하면서 해당 URL에서 {특정값}을 변수로 받아 올 수 있습니다.

## Lombok Annotation

- @NoArgsConstructor: 기본생성자를 자동으로 추가합니다.
- @AllArgsConstructor: 모든 필드 값을 파라미터로 받는 생성자를 추가합니다.
- @RequiredArgsConstructor: final이나 @NonNull인 필드 값만 파라미터로 받는 생성자를 추가합니다. final 값이 할당되면 더 이상 변경할 수 없습니다.
- @Getter: Class 내 모든 필드의 Getter method를 자동 생성합니다.
- @Setter: Class 내 모든 필드의 Setter method를 자동 생성합니다.
- @Builder: 어느 필드에 어떤 값을 채워야 할지 명확하게 정하여 생성 시점에 값을 채워줍니다.
- @Data: @Getter @Setter @EqualsAndHashCode @AllArgsConstructor을 포함한 Lombok에서 제공하는 필드와 관련된 모든 코드를 생성하는 것으로, 전체적인 모든 기능 허용으로 위험 존재하기 때문에 실제로 사용하지 않는것이 좋습니다.

```
💡 Constructor와 Builder의 차이
생성 시점에 값을 채워주는 역할은 똑같지만, Builder를 사용하면 어느 필드에 어떤 값을 채워야 할지 명확하게 인지할 수 있습니다.
해당 Class의 Builder 패턴 Class를 생성 후 생성자 상단에 선언 시 생성자에 포함된 필드만 빌더에 포함됩니다.
```

## JPA Annotation

- @Entity: 실제 DB의 테이블과 매칭될 Class임을 명시하는 것으로 테이블과 링크될 클래스임을 나타냅니다.
- @Table: Entity Class에 매핑할 테이블 정보를 알려줍니다. @Table(name = "USER")와 같은 형태로 사용되며, Annotation을 생략하면 Class 이름을 테이블 이름 정보로 매핑합니다.
- @Id: 해당 테이블의 PK 필드를 나타냅니다.
- @GeneratedValue: PK의 생성 규칙을 나타냅니다. 가능한 Entity의 PK는 Long 타입의 Auto_increment를 추천하며, 스프링 부트 2.0에선 옵션을 추가해야 auto_increment이 가능합니다. 기본값은 AUTO로, MySQL의 auto_increment와 같이 자동 증가하는 정수형 값이 됩ㄴ디ㅏ.
- @Column: 테이블의 컬럼을 나타내며, 굳이 선언하지 않더라도 해당 Class의 필드는 모두 컬럼이 됩니다. @Column을 생략하면 필드명을 사용해서 컬럼명과 매핑합니다.
