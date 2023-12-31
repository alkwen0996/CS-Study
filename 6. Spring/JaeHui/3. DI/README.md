# DI Dependency Injection 의존성 주입

DI란 Spring Framework에서 지원하는 IoC의 형태입니다. <Br>
클래스 사이의 의존관계를 Bean 설정 정보를 바탕으로 컨테이너가 자동적으로 연결해주는 것을 의미합니다. <br>
개발자는 제어를 직접 담당할 필요 없이, Bean 설정 파일에 의존 관계가 필요하다는 정보를 추가하는 형태로 구현하게 됩니다. <br>
Container가 실행 흐름의 주체가 되어 애플리케이션 코드에 의존 관계를 주입해주게 됩니다. <br>

```
✅ 의존성 Dependency 란?
현재 객체가 다른 객체와 상호작용, 즉 참조하고 있다면 다른 객체들을 현재 객체의 의존이라고 합니다.

⛔️ 의존성이 위험한 이유
하나의 모듈이 바뀌면 의존한 다른 모듈까지 변경되어야 합니다.
Unit Test 목적 자체가 다른 모듈로부터 독립적으로 테스트하는 것을 요구하기 때문에,
테스트 가능한 어플을 만들 때 의존성이 있으면 Unit Test 작성이 어렵습니다.
```

`new` 키워드를 사용해 다른 모듈을 초기화하지 않기 위해서는, 객체 생성은 다른 곳에서 하고 이미 생성된 객체를 참조하는 식으로 구현하게 됩니다. <br>
DI는 IoC 개념을 바탕으로 하여, 클래스가 외부로부터 의존성을 가져야 합니다. <br>

```
💡 DI가 필요한 이유
클래스 재사용 가능성을 높이고, 다른 클래스와 독립적으로 클래스를 테스트할 수 있도록 합니다.
비즈니스 로직의 특정 구현이 아닌 클래스를 생성하는 데 매우 효과적입니다.
```

## [DI의 3가지 방법](https://www.nextree.co.kr/p11247/)

### 1️⃣ 생성자 삽입 Contructor Injection

필요한 의존성을 모두 포함하는 클래스의 생성자를 만들고 그 생성자를 통해 의존성을 주입합니다. <br>
즉 생성자에 파라미터를 만들어두고 이를 통해 DI 컨테이너가 의존할 객체의 참조를 넘겨주는 방식입니다. <br><br>

```
✅ 생성자 주입의 장점
💡 순환 참조 방지 가능
생성자 주입은 생성자로 객체를 생성하는 시점에 생성자의 인자에 사용되는 빈을 찾거나 생성하여 빈의 생성자를 호출합니다.
그 외의 의존성 주입 방식은 빈을 먼저 생성한 후 어노테이션이 붙은 필드에 해당하는 빈을 찾아서 주입하거나 Setter의 객체를 호출해 주입하게 됩니다.
위와 같은 방식은 객체가 실제로 사용되기 전까지는 에러가 발생하지 않게 되어 문제를 찾기 어렵습니다.

💡 final 키워드
불변하는 객체를 생성할 수 있습니다.
런타임에 중에 객체가 변하는 것을 막아 불변성을 유지할 수 있어 오류를 사전에 방지할 수 있습니다.
```

### 2️⃣ setter 메소드를 이용한 매개 변수 삽입 Method(Setter) Injection

의존성을 입력 받는 setter method를 만들고 이를 통해 의존성을 주입합니다.<br>
setter 메소드는 외부에서 오브젝트 내부의 attribute 값을 변경하려는 용도로 사용됩니다. <br>
핵심 기능은 파라미터로 전달된 값을 내부의 인스턴스 변수에 저장하는 것입니다. <br>
스프링에서 지지하는 DI 방식으로, 외부에서 제공받은 오브젝트 레퍼런스를 저장해뒀다가, 내부의 메소드에서 사용하게 하는 DI 방식에 활용하기 적합합니다. <br><br>

### 3️⃣ 초기화 인터페이스를 이용한 멤버 변수 삽입 Field Injection

의존성을 주입하는 함수를 포함한 인터페이스를 작성하고 이 인터페이스를 구현하도록 함으로써 실행시에 의존성을 주입합니다.<br>
Injection을 하기 위한 인터페이스 정의 후 구현 시 DI가 이루어지도록 하는데, 이는 스프링이 지원하지 않는 방식입니다.<br>
