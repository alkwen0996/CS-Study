## 📝 Interview

#### POJO 프로그래밍에 대해 설명하세요.

```
POJO란 직역하면 오래된 방식의 간단한 자바 오브젝트라는 의미로, Java로 생성하는 순수한 객체를 의미합니다.
POJO 프로그래밍은 POJO를 이용하여 프로그래밍 코드를 작성하는 것입니다.
순수 자바 객체만을 사용한다고 해서 POJO 프로그래밍이라고 볼 수는 없고, 기본적인 규칙들을 지켜야 합니다.
Spring에서 POJO는 IoC/DI, AOP, PSA를 통해 달성할 수 있습니다.

1️⃣ Java나 Java 스펙에 정의된 것 이외에는 다른 기술이나 규약에 얽매이지 않아야 합니다.
자바 이외에 웹 프레임워크에서 지원하는 클래스 등을 사용하게 되면, 기술을 변경해야 할 때 객체지향 설계 기법을 적용하기 어려워지기 때문입니다.

2️⃣ 특정 환경에 종속적이지 않아야 합니다.
특정한 프레임워크에서만 동작이 가능하면 안된다는 의미로, 환경에 독립적이어야 합니다.
따라서 웹 기반의 환경 정보나 웹 기술을 담고 있는 클래스 또는 인터페이스를 사용하면 안됩니다.
```

<br>

#### IoC란 무엇인가요?

```
IoC란 직역하면 제어의 역전이라는 의미로, 제어권이 사용자에게 있지 않고 프레임워크에 있는 것을 의미합니다.
객체의 생성부터 생명 주기의 관리까지 모든 객체에 대한 제어권이 바뀐 것으로, 대부분의 프레임워크에서 사용하는 방법입니다.
개발자는 프레임워크에 필요한 부분을 개발해서 끼워 넣기의 형태로 조립하는 방식의 개발을 하게 됩니다.
이렇게 조립된 코드의 최종 호출은 프레임워크 내부에서 결정된 대로 이루어지는 것을 제어의 역전이라고 표현합니다.
Spring Framework에서 지원하는 IoC Container는 POJO의 생명주기를 관리하며, 생성된 인스텐스들에게 추가적인 기능들을 제공합니다.
```

<br>

#### Library와 Framework의 차이에 대해 설명하세요.

```
IoC가 적용된 것을 Framework라고 합니다.
라이브러리는 애플리케이션의 흐름을 개발자가 직업 제어하고, 동작 중에 필요한 기능이 있을 때 능동적으로 라이브러리를 사용하는 형태입니다.
프레임워크는 애플리케이션 코드가 프레임워크에 의해 사용됩니다.
프레임워크 위에 개발한 클래스를 등록한 뒤, 프레임워크가 흐름을 주도하는 중에 개발자가 만든 애플리케이션 코드를 사용하도록 만드는 방식입니다.
```

<br>

#### DI란 무엇인지 설명하고, 그 중 생성자 주입에 대해 자세하게 설명해주세요.

```
DI란 Spring Framework에서 지원하는 IoC의 형태입니다.
클래스 사이의 의존관계를 Bean 설정 정보를 바탕으로 컨테이너가 자동적으로 연결해주는 것을 의미합니다.
개발자는 제어를 직접 담당할 필요 없이, Bean 설정 파일에 의존 관계가 필요하다는 정보를 추가하는 형태로 구현하게 됩니다.
Container가 실행 흐름의 주체가 되어 애플리케이션 코드에 의존 관계를 주입해주게 됩니다.

생성자 주입은 필요한 의존성을 모두 포함하는 클래스의 생성자를 만들고 그 생성자를 통해 의존성을 주입합니다.
즉 생성자에 파라미터를 만들어두고 이를 통해 DI 컨테이너가 의존할 객체의 참조를 넘겨주는 방식입니다.

💡 순환 참조 방지 가능
생성자 주입은 생성자로 객체를 생성하는 시점에 생성자의 인자에 사용되는 빈을 찾거나 생성하여 빈의 생성자를 호출합니다.

💡 final 키워드
불변하는 객체를 생성할 수 있습니다.
런타임에 중에 객체가 변하는 것을 막아 불변성을 유지할 수 있어 오류를 사전에 방지할 수 있습니다.
```

<br>

#### Spring Framework와 Spring Boot의 차이에 대해 설명하세요.

```
Spring Framework란 자바 엔터프라이즈 개발을 편하게 해주는 경량급 오픈소스 애플리케이션 프레임워크입니다.
POJO 기반의 Enterprise Application 개발을 쉽고 편하게 할 수 있도록 하는 것이 목표입니다.
자바 애플리케이션을 개발하는 데 필요한 하부 구조(Infrastructure)를 포괄적으로 제공하기 때문에, 개발자는 개발에 집중할 수 있습니다.
동적인 웹 사이트를 개발하기 위한 여러가지 서비스를 제공하며,
대한민국 공공기관의 웹 서비스 개발 시 사용을 권장하고 있는 전자 정보 표준 프레임워크의 기반 기술입니다.

하지만 Spring Legacy 프로젝트는 denpendency를 설정해줄 때 설정 파일이 매우 길고,
모든 denpendency에 대해 버전 관리를 하나 하나 직접 해주어야 하는 번거로움이 있습니다.
또한 configuration 설정을 할 때도 모든 어노테이션 및 Bean 등록 등을 직접 설정해야 합니다.

Spring Boot는 이를 보완하기 위해 스프링으로 애플리케이션을 만들 때 필요한 설정을 간편하게 처리해주는 별도의 프레임워크입니다.
설정 정보를 간략화할 수 있는 이유는 Spring Boot가 기존 복잡한 설정을 대신하고 있기 때문입니다.
초기 설정에 쏟아야 하는 시간과 노력을 절약하여 개발자는 비즈니스 로직을 구현하는 데에 집중할 수 있습니다.

또한 기존 배포 시 별도의 외장 웹 서버를 설치 후 프로젝트를 war 파일로 필드해야 해서 느리고 번거로웠습니다.
Spring Boot는 자체적인 웹 서버를 내장하고 있어 빠르고 간편하게 배포를 진행할 수 있습니다.
독립적으로 실행 가능한 jar 파일로 프로젝트를 빌드할 수 있어 클라우드 서비스 및 도커와 같은 가상화 환경에 빠르게 배포할 수 있습니다.
```

<br>

#### Spring에서 Bean 과 Container에 대해 설명하세요.

```
컨테이너에 담겨있으며, 필요할 때 컨테이너에서 가져와서 사용하게 됩니다.
@Bean을 사용하거나 xml 설정을 통해 일반 객체를 Bean으로 등록할 수 있고, Bean으로 등록된 객체는 쉽게 주입하여 사용 가능합니다.

컨테이너란 인스턴스의 생명주기를 관리하며, 생성된 인스턴스들에게 추가적인 기능을 제공하도록 하는 것을 의미합니다.
개발자가 작성한 코드의 처리 과정을 위임받은 독립적인 객체라고 생각하면 됩니다.
적절한 설정만 되어 있다면 누구의 도움 없이도 개발자가 작성한 코드를 스스로 참조한 뒤 알아서 객체의 생성과 소멸을 컨트롤합니다.
Spring Framework는 다른 프레임워크들과 달리 컨테이너 기능을 제공하는데, 이를 제공 가능하도록 하는 것이 IoC 패턴입니다.
스프링 컨테이너에는 BeanFactory, ApplicationContext 인터페이스가 있습니다.

💡 Spring Container & Bean
AppConfig 클래스 같은 것이 스프링 컨테이너로 @Configuration 사용합니다.
AppConfig 내에서 @Bean이 붙은 것이 Spring Bean을 의미합니다.
```

<br>

#### Bean 초기화 방법 중 권장되는 방법에 대해 설명해 주세요.

```
1️⃣ 사용 방법이 간결하며 코드에서 초기화 메소드가 존재함을 쉽게 파악 가능하여 xml 설정 방법보다 직관적입니다. (권장)
초기화: 빈 초기화 메소드에 @PostConstruct 사용하여 xml에 <context:annotation-config></context:annotation-config> 추가
소멸: 빈 소멸 메소드에 `@PreDestroy` 사용하여 xml에 <context:annotation-config></context:annotation-config> 추가
```

<br>

#### MVC1 패턴과 MVC2 패턴의 차이에 대해 설명하세요.

```
MVC1 패턴은 JSP 페이지에서 View와 Controller 역할 담당하여 로직 처리를 하게 됩니다.
구조는 단순하지만, JSP 내에서 html과 자바 코드가 함께 사용되어 복잡하고 유지보수가 어렵습니다.

MVC2 패턴은 Model, View, Controller로 모듈화된 형태로, JSP는 로직 처리 없이 Client에게 보여지는 View만 담당하게 됩니다.
구조가 복잡하나 유지보수가 용이합니다.
```

<br>

#### DAO, DTO, VO 차이에 대해 설명하세요.

```
DAO(Data Access Object)
DB의 데이터를 조회하거나 조작하는 기능을 전담하도록 만든 객체를 말합니다.
DB에 접근을 하기위한 로직과 비즈니스 로직을 분리하기 위해서 사용합니다.

DTO(Data Transfer Object)
계층간 데이터 교환을 위한 자바 Bean들을 말합니다.
여기서 말하는 계층은 Controller, View, Business Layer, Persistent Layer 입니다.
일반적인 DTO는 로직을 갖고 있지 않는 순수한 데이터 객체이며, 속성과 그 속성에 접근하기 위한 getter, setter 메소드만 가진 클래스입니다.

VO(Value Object)
DTO와 동일한 개념이지만 read only 속성을 가지는 객체입니다.
```

<br>

#### Spring Annotation에 대해 몇 가지 설명해주세요.

```
- @ComponentScan: @Service, @Repository, @Controller, @Configuration이 붙은 클래스 Bean들을 찾아서 Context에 bean등록을 해주는 Annotation
- @Component: 개발자가 직접 작성한 Class를 Bean으로 등록하기 위한 Annotation
- @Bean: 개발자가 직접 제어가 불가능한 외부 라이브러리등을 Bean으로 만들려할 때 사용되는 Annotation
- @Autowired: 속성(field), setter method, constructor(생성자)에서 사용하며 Type에 따라 알아서 Bean을 주입해주는 것입니다.
- @Inject: @Autowired 어노테이션과 비슷한 역할
- @Controller: Spring의 Controller로 Spring MVC에서 Controller클래스에 쓰입니다.
- @RestController: Spring에서 Controller 중 View로 응답하지 않는, Controller를 의미합니다.
- @Service: Service Class에서 쓰이는 것으로, 비즈니스 로직을 수행하는 Class라는 것을 나타내는 용도입니다.
- @Repository: DAO class에서 쓰이며, DataBase에 접근하는 method를 가지고 있는 Class에서 쓰입니다.
- @CrossOrigin: CORS 보안상의 문제로 브라우저에서 리소스를 현재 origin에서 다른 곳으로의 AJAX요청을 방지하는 것입니다.
- @RequestBody: 요청이 온 데이터(JSON이나 XML형식)를 바로 Class나 model로 매핑하기 위한 Annotation입니다.
- @PathVariable: method parameter 앞에 사용하면서 해당 URL에서 {특정값}을 변수로 받아 올 수 있습니다.
```

<br>

#### @Controller 와 @RestController 의 차이에 대해 설명하세요.

```
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

<br>

#### Lombok Annotation에 대해 몇 가지 설명해주세요.

```
- @NoArgsConstructor: 기본생성자를 자동으로 추가합니다.
- @AllArgsConstructor: 모든 필드 값을 파라미터로 받는 생성자를 추가합니다.
- @RequiredArgsConstructor: final이나 @NonNull인 필드 값만 파라미터로 받는 생성자를 추가합니다. final 값이 할당되면 더 이상 변경할 수 없습니다.
- @Getter: Class 내 모든 필드의 Getter method를 자동 생성합니다.
- @Setter: Class 내 모든 필드의 Setter method를 자동 생성합니다.
- @Builder: 어느 필드에 어떤 값을 채워야 할지 명확하게 정하여 생성 시점에 값을 채워줍니다.
- @Data: @Getter @Setter @EqualsAndHashCode @AllArgsConstructor을 포함한 Lombok에서 제공하는 필드와 관련된 모든 코드를 생성하는 것으로, 전체적인 모든 기능 허용으로 위험 존재하기 때문에 실제로 사용하지 않는것이 좋습니다.
```

<br>

#### JPA Annotation에 대해 설명해주세요.

```
- @Entity: 실제 DB의 테이블과 매칭될 Class임을 명시하는 것으로 테이블과 링크될 클래스임을 나타냅니다.
- @Table: Entity Class에 매핑할 테이블 정보를 알려줍니다. @Table(name = "USER")와 같은 형태로 사용되며, Annotation을 생략하면 Class 이름을 테이블 이름 정보로 매핑합니다.
- @Id: 해당 테이블의 PK 필드를 나타냅니다.
- @GeneratedValue: PK의 생성 규칙을 나타냅니다. 가능한 Entity의 PK는 Long 타입의 Auto_increment를 추천하며, 스프링 부트 2.0에선 옵션을 추가해야 auto_increment이 가능합니다. 기본값은 AUTO로, MySQL의 auto_increment와 같이 자동 증가하는 정수형 값이 됩ㄴ디ㅏ.
- @Column: 테이블의 컬럼을 나타내며, 굳이 선언하지 않더라도 해당 Class의 필드는 모두 컬럼이 됩니다. @Column을 생략하면 필드명을 사용해서 컬럼명과 매핑합니다.
```

<br>

#### Constructor와 Builder의 차이점에 대해 설명하세요.

```
생성 시점에 값을 채워주는 역할은 똑같지만, Builder를 사용하면 어느 필드에 어떤 값을 채워야 할지 명확하게 인지할 수 있습니다.
해당 Class의 Builder 패턴 Class를 생성 후 생성자 상단에 선언 시 생성자에 포함된 필드만 빌더에 포함됩니다.
```

<br>

#### Restful API에 대해 설명하세요.

```
HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고,
HTTP Method(POST, GET, PUT, DELETE, PATCH 등)를 통해
해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미합니다.
CRUD는 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능인 Create(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말입니다.
```
