# [Annotation](http://asfirstalways.tistory.com/309)

어노테이션이란 사전적으로는 주석이라는 의미로, 주석처럼 코드에 명시하여 클래스에 특별한 의미를 부여하거나 기능을 주입할 수 있는 기능입니다. <br>
인터페이스를 기반으로 한 문법이며, `Built-In Annotation`, `Meta Annotation`, `Custom Annotation` 세 종류로 구분할 수 있습니다. <br>

## Built-In Annotation

Java에 내장되어 있는 어노테이션으로 주로 컴파일러에게 유용한 정보를 제공하는 역할을 합니다. <br>

```java
@Override // 메서드 앞에만 붙일 수 있으며 현재 메서드가 Super 클래스의 메소드를 오버라이드한 메소드임을 컴파일러에게 명시합니다. 오타 발생 가능성을 잡아줄 수 있습니다.
@Deprecated // 더 이상 사용하지 않는 메소드를 나타냅니다.
@SupressWarning // 프로그래머의 의도를 컴파일러에게 전달하여 경고를 제거합니다.
@FunctionalInterface // 함수형 인터페이스라는 것을 알리고 검사하는 기능을 제공합니다. 개발자의 실수를 방지할 수 있습니다.
```

## Meta Annotation

어노테이션에 사용되는 어노테이션으로 해당 어노테이션의 동작 대상을 결정합니다. <br>
주로 새로운 어노테이션을 정의할 때 사용합니다. <br>

```java
@Target // 어노테이션이 적용가능한 대상을 지정하는데 사용합니다. 여러 개 값을 지정할 때는 {}를 사용합니다.
@Retention // 어노테이션이 유지되는 기간을 지정할 수 있습니다. SOURCE / CLASS / RUNTIME
@Documented // 어노테이션에 대한 정보가 JavaDoc으로 작성한 문서에 포함되도록 할 때 사용하는 어노테이션으로 대부분의 Built-In Annotation에 붙어 있습니다. (@Override, @SuppressWarnings 제외)
@Inherited // 어노테이션이 자손 클래스에도 상속되도록 하는 어노테이션으로, 조상 클래스에 붙이면 자손 클래스도 이 어노테이션이 붙은 것과 같이 인식됩니다.
@Native // JVM이 설치된 OS의 네이티브 메서드에 의해 참조되는 상수 필드에 붙이는 어노테이션입니다. 대표적으로 Object 클래스의 메서드들이 네이티브 메서드에 해당되며, 네이티브 메서드와 자바에 정의된 메서드를 연결하는 것을 JNI(Java Native Interface)라고 합니다.
```

## Custom Annotation

직접 어노테이션 타입을 선언하는 것으로 특별한 종류의 인터페이스입니다. <br>
일반적인 인터페이스 선언과 구분하기 위해 `interface` 앞에 `@`를 붙여 사용합니다. <br>
어노테이션 타입은 암묵적으로 `java.lang.annotation.Annotation`을 확장하기 때문에 `extends`절을 가질 수 없습니다. <br>

```java
💡 Marker Annotation
요소가 한 개도 없으며 단순히 표식으로서 사용되는 어노테이션으로, 컴파일러에게 의미를 전달하는 데 사용합니다.

💡 Single-value Annotation
요소로 단일 변수만을 갖는 어노테이션으로, 단일 변수밖에 없기 때문에 값만을 명시하여 데이터를 전달할 수 있습니다.

@interface MyAnnotation {
  String value();
}
@MyAnnotation("passed") // @MyAnnotation(value="passed")와 동일
class Newclass { ... }

💡 Full Annotation
요소로 둘 이상의 변수를 갖는 어노테이션으로, 데이터를 배열 안에 key-value의 형태로 전달합니다.
- 요소 타입은 Primitive Type, String, Enum, Annotation, Class만 허용됩니다. 각 요소는 기본값을 가질 수 있습니다.
- 요소의 () 안에 매개변수를 선언할 수 없습니다.
- 예외를 선언할 수 없습니다.
- 요소를 타입 매개변수로 정의할 수 없습니다.

int count() default 1;
```
