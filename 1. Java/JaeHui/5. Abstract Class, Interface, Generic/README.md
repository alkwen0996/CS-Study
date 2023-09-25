# Abstract Class, Interface, Generic

## Abstract Class

추상 메소드란 자식 클래스에서 반드시 오버라이딩해야만 사용할 수 있는 메소드를 의미합니다. <br>
추상 메소드가 포함된 클래스를 상속받는 자식 클래스가 반드시 추상 메소드를 구현하도록 하기 위해 사용합니다. <br>
예를 들어 중복 또는 공통적인 부분을 미리 만들어진 것을 사용하고 자신에게 필요한 부분만을 재정의하여 사용함으로써 생산성이 향상되고 배포 등이 쉬워지기 때문입니다. <br>
추상 메소드는 선언부만 존재하면 구현부는 작성하지 않습니다. <br>
이 작성되어 있지 않은 구현부를 자식 클래스에서 오버라이딩하여 사용하게 됩니다. <br>

```java
abstract int fun();
```

위와 같이 선언부만 있고 구현부가 없다는 의미로 선언부 끝에 세미콜론(;)을 추가합니다.<br><br>

[추상 클래스](http://www.tcpschool.com/java/java_polymorphism_abstract)란 하나 이상의 추상 메소드를 포함하는 클래스를 가리켜 추상 클래스하고 합니다. <br>
객체 지향 프로그래밍에서 중요한 특징인 다형성을 가지는 메소드의 집합을 정의할 수 있도록 해줍니다. <br>
즉 반드시 사용되어야 하는 메소드를 추상 클래스에 추상 메소드로 선언해 놓으면, 이 클래스를 상속받는 모든 클래스에서는 이 추상 메소드를 반드시 재정의해야 합니다. <br>
구현의 강제를 통해 프로그램의 안정성을 향상시킬 수 있습니다. <br>

```java
abstract class A {
  ...
  abstract int fun();
  ...
}
```

이러한 추상 클래스는 동작이 정의되어 있지 않은 추상 메소드를 포함하고 있으므로, 인스턴스를 생성할 수 없습니다. <br>
상속을 통해 자식 클래스를 만든 후, 자식 클래스에서 추상 클래스의 모든 추상 메소드를 오버라이딩하고 나서 인스턴스를 생성할 수 있게 됩니다. <br>

```java
abstract class Animal { abstract void cry(); }
class Cat extends Animal { void cry() { System.out.println("냐옹냐옹!"); } }
class Dog extends Animal { void cry() { System.out.println("멍멍!"); } }

public class Polymorphism02 {
    public static void main(String[] args) {
        // Animal a = new Animal(); // 추상 클래스는 인스턴스를 생성할 수 없음.
        Cat c = new Cat();
        Dog d = new Dog();

        c.cry();
        d.cry();
    }
}
```

## Interface

자바에서는 메소드 출처의 모호성 등의 문제로 인해 클래스를 통한 다중 상속이 지원되지 않습니다. <br>
이를 보완하기 위해 인터페이스라는 것을 통해 다중 상속을 지원합니다. <br>
[인터페이스](http://www.tcpschool.com/java/java_polymorphism_interface)란 다른 클래스를 작성할 때 기본이 되는 틀을 제공하면서, <br>
다른 클래스 사이의 중간 매개 역할까지 담당하는 일종의 추상 클래스를 의미합니다. <br>

```
✅ Abstract Class vs Interface
추상 클래스는 추상 메소드뿐만 아니라 생성자, 필드, 일반 메소드도 포함할 수 있지만,
인터페이스는 최고 수준의 추상화 단계로, 오로지 추상 메소드와 상수만을 포함할 수 있습니다.
JDK 8부터 인터페이스에서 default method와 static method를 통해 구현부도 작성할 수 있게 되었습니다.
```

## Generic

[제네릭](http://www.tcpschool.com/java/java_generic_concept)이란 데이터의 타입을 일반화한다는 것을 의미합니다. <br>
클래스나 메소드에서 사용할 내부 데이터 타입을 컴파일 시에 미리 지정하는 방법으로, 컴파일 시 미리 타입 검사를 수행하게 됩니다. <br>
이로써 클래스나 메소드 내부에서 사용되는 객체의 타입 안정성을 높일 수 있고, 반환값에 대한 타입 변환 및 타입 검사에 들어가는 노력을 줄일 수 있습니다. <br><br>

JDK 1.5이전에서는 여러 타입을 사용하는 대부분의 클래스나 메소드에서 인수나 반환값으로 Object 타입을 사용했으나, 반환된 객체를 다시 원하는 타입으로 변환해야 하며 이 때 오류가 발생할 수 있습니다. <br>
이를 보완하기 위해 JDK 1.5부터 도입된 제네릭을 통해 컴파일 시에 미리 타입이 정해져 번거로운 작업을 생략할 수 있게 됩니다. <br><br>

제네릭 클래스의 선언은 다음과 같이 할 수 있습니다. <br>

```java
class MyArray<T> {
    T element;
    void setElement(T element) { this.element = element; }
    T getElement() { return element; }
}
```

`T`를 타입 변수(type variable)라고 하며, 임의의 참조형 타입을 의미합니다.<br>
어떠한 문자를 사용해도 상관없으며, 여러 개의 타입 변수는 쉼표(,)로 구분하여 명시할 수 있습니다.<br>
타입 변수는 클래스에서뿐만 아니라 메소드의 매개변수나 반환값으로도 사용할 수 있습니다. <br><br>

제네릭 클래스를 생성할 때는 다음과 같이 타입 변수 자리에 실제 사용할 타입을 명시해야 합니다. <br>

```java
MyArray<Integer> myArr = new MyArray<Integer>();
```

이렇게 실제 사용할 타입을 명시하면 내부적으로는 정의된 타입 변수가 명시된 실제 타입으로 변환되어 처리됩니다. <br>
타입을 명시할 때 기본 타입을 바로 사용할 수 없고, Wrapper Class를 사용해야 합니다. <br><br>

Java SE 7부터 인스턴스 생성 시 타입을 추정할 수 있는 경우 타입을 생략할 수 있습니다. <br>

```java
MyArray<Integer> myArr = new MyArray<Integer>();
```

제네릭 타입은 컴파일 시 컴파일러에 의해 자동으로 검사되어 타입 변환됩니다. <br>
이 때 코드 내의 모든 제네릭 타입은 제거되어 컴파일된 클래스 파일에는 어떠한 제네릭 타입도 포함되지 않게 됩니다. <br>
제네릭을 사용하지 않는 코드와의 호환성을 유지하기 위해 이렇게 동작됩니다. <br>

```
💡 Java Generic vs C++ Template
- Template에는 int와 같은 기본 타입을 인자로 넘길 수 있지만, Generic에서는 Integer을 대신 사용해야 합니다.
- Template은 인자로 주어진 타입으로부터 객체를 만들어 낼 수 있지만, Generic에서는 불가능합니다.
- Generic Class로 만든 모든 객체는 전부 동등한 타입이지만, Template는 다른 타입 인자 사용 시 서로 다른 타입의 객체입니다.
- Generic은 타입 인자를 특정한 타입이 되도록 제한할 수 있습니다.
- Generic은 정적 메서드나 변수를 선언하는 데 사용할 수 없지만, Template는 가능합니다.
```
