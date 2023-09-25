# Wrapper Class

프로그램에 따라 기본형의 데이터를 객체로 취급해야 하는 경우 사용하는 클래스입니다.<br>

```java
- boolean -> Boolean
- byte -> Byte
- short -> Short
- int -> Integer
- long -> Long
- float -> Float
- double -> Double
- char -> Character
```

래퍼 클래스는 각각의 타입에 해당하는 데이터를 인수로 전달받아 해당 값을 가지는 객체로, 모두 java.lang 패키지에 포함되어 제공됩니다.<br>
산술 연술 연산을 위해 정의된 클래스가 아니므로 인스턴스의 저장된 값을 변경할 수 없고, 단지 값을 참조하기 위해 새로운 인스턴스를 생성하게 됩니다. <br>
기본 타입의 데이터를 래퍼 클래스의 인스턴스로 변환하는 과정을 박싱(Boxing), 래퍼 클래스의 인스턴스에 저장된 값을 다시 기본 타입의 데이터로 꺼내는 과정을 언박싱(Unboxing)이라고 합니다. <br>
JDK 1.5부터 박싱과 언박싱이 필요한 상황에 자바 컴파일러가 이를 자동으로 처리해줍니다. <br>

## Auto Boxing & Auto Unboxing

오토 박싱을 이용하면 new 키워드를 사용하지 않고도 자동으로 인스턴스를 생성할 수 있습니다. <br>
또한 오토 언박싱을 이용하여 인스턴스에 저장된 값을 바로 참조할 수 있습니다. <br>

```java
Integer num = new Integer(17); // 박싱
int n = num.intValue();        // 언박싱
System.out.println(n); // 출력 값: 17


Character ch = 'X'; // Character ch = new Character('X'); : 오토박싱
char c = ch;        // char c = ch.charValue();           : 오토언박싱
System.out.println(c); // 출력 값: X
```

래퍼 클래스의 비교 연산도 오토언박싱을 통해 가능해지지만, 인스턴스에 저장된 값의 동등 여부 판단은 비교 연산자인 동등 연산자(==)를 사용해서는 안 되며, equals() 메소드를 사용해야만 합니다. <br>
래퍼 클래스도 객체이므로 동등 연산자(==)를 사용하게 되면, 두 인스턴스의 값을 비교하는 것이 아니라 두 인스턴스의 주소값을 비교하게 됩니다. <br>
따라서 서로 다른 두 인스턴스를 동등 연산자(==)로 비교하게 되면, 언제나 false 값을 반환합니다. <br>
그러므로 인스턴스에 저장된 값의 동등 여부를 정확히 판단하려면 equals() 메소드를 사용해야 합니다. <br>
