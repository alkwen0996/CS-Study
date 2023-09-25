# Container

컨테이너란 인스턴스의 생명주기를 관리하며, 생성된 인스턴스들에게 추가적인 기능을 제공하도록 하는 것을 의미합니다. <br>
개발자가 작성한 코드의 처리 과정을 위임받은 독립적인 객체라고 생각하면 됩니다. <br>
적절한 설정만 되어 있다면 누구의 도움 없이도 개발자가 작성한 코드를 스스로 참조한 뒤 알아서 객체의 생성과 소멸을 컨트롤합니다. <br>
Spring Framework는 다른 프레임워크들과 달리 컨테이너 기능을 제공하는데, 이를 제공 가능하도록 하는 것이 IoC 패턴입니다. <br>
스프링 컨테이너에는 `BeanFactory`, `ApplicationContext` 인터페이스가 있습니다.<br>

```
💡 Spring Container & Bean
AppConfig 클래스 같은 것이 스프링 컨테이너로 @Configuration 사용합니다.
AppConfig 내에서 @Bean이 붙은 것이 Spring Bean을 의미합니다.
```

```
✅ ApplicationContext
스프링 컨테이너로, BeanFactory 인터페이스의 하위 인터페이스압니다.
BeanFactory는 스프링 컨테이너의 최상위 인터페이스로 ApplicationContext는 BeanFactory에 부가 기능을 추가한 것입니다.
```
