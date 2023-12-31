## 📝 Interview

#### 🗨 객체 지향의 특징에 대해 설명해주세요.

```
1. 추상화 Abstraction: 현실의 객체를 추상화하여 클래스를 구성하는 것으로, 객체에서 공통된 속성이나 기능을 추출하는 것을 의미합니다. 중요한 것, 관심 대상인 것만을 강조해서 추출함으로써 프로그램의 복잡도를 관리할 수 있으며, 관점에 따라 추상화의 결과가 달라질 수 있습니다.
2. 캡슐화 Encapsulation: 데이터 은닉과 보호를 위해 데이터를 외부에 직접 노출시키지 않고 메서드를 이용해 보호하는 특징을 말합니다. 내부의 데이터나 함수를 외부에서 참조하지 못하도록 차단하는 개념을 정보 은닉(Information Hiding)이라 하고, 이를 위해 관심있는 데이터와 기능을 모아 패킹한 것을 캡슐화라고 합니다.
3. 다형성 Polymorphism: 하나의 객체를 여러 가지 타입으로 참조할 수 있는 특징입니다. 같은 코드라하더라도 상항에 따라 다른 방식으로 동작하는 성질로 Java에서 대표적으로 Overriding과 Overloading이 있습니다.
4. 상속 Inheritance: 부모 클래스의 자산을 물려받아 자식을 정의함으로써 코드의 재사용이 가능하다는 특징입니다.
```

<br>

#### 🗨 Promotion와 casting의 차이에 대해 설명해주세요.

```
변수의 데이터 타입을 바꿔주는 타입변환의 방식에는 자동 형변환(Promotion)과 강제 형변환(Casting)이 있습니다.
자동 형변환은 묵시적 타입 변환, 강제 형변환은 명시적 타입 변환이라고도 합니다.
묵시적 형변환이란 프로그램 실행 도중에 자동적으로 형변환이 일어나는 것으로(JVM),
아래 코드와 같이 작은 메모리의 크기의 데이터 타입을 큰 메모리 크기의 데이터 타입으로 변환하는 행위를 말합니다.
강제 형변환은 특정 조건을 갖추지 못했지만 강제로 형변환을 하고 싶을 때 사용하는 방법입니다.
```

<br>

#### 🗨 Wrapper Class를 사용하는 이유에 대해 설명해주세요.

```
프로그램에 따라 기본형의 데이터를 객체로 취급해야 하는 경우 사용하는 클래스입니다.
래퍼 클래스는 각각의 타입에 해당하는 데이터를 인수로 전달받아 해당 값을 가지는 객체로, 모두 java.lang 패키지에 포함되어 제공됩니다.
산술 연술 연산을 위해 정의된 클래스가 아니므로 인스턴스의 저장된 값을 변경할 수 없고, 단지 값을 참조하기 위해 새로운 인스턴스를 생성하게 됩니다.
기본 타입의 데이터를 래퍼 클래스의 인스턴스로 변환하는 과정을 박싱(Boxing), 래퍼 클래스의 인스턴스에 저장된 값을 다시 기본 타입의 데이터로 꺼내는 과정을 언박싱(Unboxing)이라고 합니다.
JDK 1.5부터 박싱과 언박싱이 필요한 상황에 자바 컴파일러가 이를 자동으로 처리해줍니다.
```

<br>

#### 🗨 Abstract Class와 Interface 차이점에 대해 설명해주세요.

```
추상 클래스는 추상 메소드뿐만 아니라 생성자, 필드, 일반 메소드도 포함할 수 있지만,
인터페이스는 최고 수준의 추상화 단계로, 오로지 추상 메소드와 상수만을 포함할 수 있습니다.
JDK 8부터 인터페이스에서 default method와 static method를 통해 구현부도 작성할 수 있게 되었습니다.
```

#### 🗨 Java 컴파일 과정에 대해 설명해주세요.

```
1. 개발자가 자바 소스코드(.java)를 작성합니다.
2. 자바 컴파일러(Compiler)가 자바 소스파일을 컴파일하고 이때 자바 바이트 코드 파일(.class)이 생성됩니다. 이는 자바 가상 머신이 이해할 수 있는 코드로, 각 명령어는 1byte 크기의 Opcode와 추가 피연산자로 이루어집니다.
3. 바이트 코드를 JVM의 클래스 로더(Class Loader)로 전달합니다.
4. 클래스 로더는 동적 로딩(Dynamic Loading)을 통해 필요한 클래스들을 로딩 및 링크하여 런타임 데이터 영역(Runtime Data Area)인 JVM의 메모리에 올립니다.
```

<br>

#### 🗨 Java 버전별 특징에 대해 설명해주세요.

| 버전      | 출시년월 | 특징                                                                                                                                                                                                                                                                                 |
| --------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| JDK 1.0a2 | 1995.05  | 언어 자체가 정식적으로 발표된 날이며, Oak라는 명칭으로 불리었습니다.                                                                                                                                                                                                                 |
| JDK 1.0   | 1996.01  | 안정화 작업을 거친 1.0.2 버전에서 Java로 이름이 바뀌었습니다.                                                                                                                                                                                                                        |
| Java SE 6 | 2006.12  | J2SE에서 Java SE로 표기가 바뀌었습니다. <br> 가비지 컬렉터 G1(Garbage First) GC를 테스트용으로만 사용하도록 추가하였습니다.                                                                                                                                                          |
| Java SE 8 | 2014.03  | 오라클 인수 후 첫 번째 버전으로, Oracle JDK, OpenJDK 2개 버전으로 나뉩니다. <br> Lambda Expression, Method Referense, Interface의 Default Methods, Null 처리 Optional, <br>Clock, ZoneId, LocalDate 등의 날짜와 시간 API, Stream API 등이 추가되었고, PermGen Area가 제거되었습니다. |

<br>

#### 🗨 call by value와 call by reference의 차이점과 Java에서 어떻게 동작하는지 설명해주세요.

```
call by value는 함수 호출 시 전달되는 변수 값을 복사해서 함수 인자로 전달하는 것으로,
복사된 인자는 힘수 안에서 지역적으로 사용되기 때문에 local value 속성을 가집니다.
따라서 함수 안에서 인자 값이 변경되더라도 외부 변수 값은 변경되지 않습니다.
원본의 데이터가 변경될 가능성이 없지만 인자를 넘겨줄 때마다 메모리 공간을 할당해야 해서 메모리 공간을 더 사용하게 됩니다.

call by reference는 함수 호출 시 인자로 전달되는 변수의 레퍼런스를 전달합니다.
따라서 함수 안에서 인자 값이 변경되면 argument로 전달된 객체의 값도 변경됩니다.
메모리 공간 할당 문제는 해결되었지만 원본 값이 변경될 수 있다는 위험이 존재합니다.

자바의 경우 항상 call by value로 값을 넘깁니다.
C, C++와 같이 변수의 주소값 자체를 가져오거나 넘길 수 있는 방법이 없습니다.
reference type 을 넘길 시 해당 객체의 주소값을 복사하여 이를 가지고 사용하게 됩니다.
따라서 원본 객체의 프로퍼티까지는 접근이 가능하나 원본 객체 자체를 변경할 수는 없습니다.
```

#### 🗨 static, final, static final에 대해 설명해주세요.

```
static은 객체 생성 없이 사용할 수 있는 필드와 메소드를 생성하고자 할 때 활용하는 것으로, static 키워드를 통해 사용할 수 있습니다.
객체마다 가질 필요가 없는 공용으로 사용하는 필드 또는 인스턴스 필드를 포함하지 않는 메소드에 사용합니다.
정적 메소드는 객체 참조 없이 바로 사용할 수 있기 때문에 인스턴스 필드나 메소드, this 키워드를 사용할 수 없습니다.

final 키워드를 사용하면 해당 변수는 값이 최종적인 값이 되므로 수정이 불가능합니다.
값을 지정하는 방법은 선언과 동시에 값을 할당하거나, 생성자에 의해 값을 할당하는 2가지 방법이 있습니다.

static 키워드와 final 키워드를 함께 사용하면 상수를 선언할 수 있습니다.
상수랑 변하지 않는 값을 뜻하는데, final 키워드만 사용할 경우 값이 다를 수 있기 때문에 static final로 선언해야 합니다.
```

<br>

#### 🗨 Java와 다른 언어와의 차이점을 비교해주세요.

```
✅ Java
객체 지향 언어이며, 인터프리터와 컴파일러를 모두 사용합니다.
Javac(Java Compiler)를 이용해 소스코드를 .class 파일로 컴파일 한 후, JVM의 인터프리터에서 바이트코드를 한 줄씩 읽어 실행합니다.
Gabage Collector가 존재하며, 웹 서비스, 백엔드 서버, 안드로이드 앱 개발에 주로 사용됩니다.

✅ C
절차 지향형 언어로, 코드들이 일련의 순서를 가지고 수행되는 것이 중요합니다.
함수들의 순차적인 진행이 이루어지는 식으로 프로그램이 동작하게 됩니다.
컴파일러 언어이며 호환성이 뛰어나고 Low Level 언어의 특징을 가집니다.
어셈블리어 수준으로 하드웨어를 제어할 수 있기 때문에 임베디드 시스템, 운영체제, 하드웨어 제어 시스템 개발 등에 사용됩니다.
Java의 Garbage Collection과 다르게 개발자가 시스템 자원을 직접 제어해야 합니다.

✅ C++
객체 지향 언어이며, C언어의 문법적 체계를 그대로 계승 후 객체 지향의 개념을 도입한 언어입니다.
C언어와 마찬가지로 컴파일러를 사용하며 타입 체크를 엄격히 하여 런타임 에러의 가능성을 줄였습니다.
인라인 함수의 도입 등으로 실행 시간 호율성 저하를 최소화하는 특징이 있습니다.

✅ Python
객체지향, 스크립트, 인터프리터 언어이며, 동적 타입 언어이고 플랫폼에 독립적입니다.
확장성과 이식성이 높으며 Garbage Collection을 지원합니다.
딥러닝, 빅데이터, AI 개발등에 주로 사용됩니다.
```

<br>

#### 🗨 Java Generic와 C++ Template을 비교 설명해주세요.

```
- Template에는 int와 같은 기본 타입을 인자로 넘길 수 있지만, Generic에서는 Integer을 대신 사용해야 합니다.
- Template은 인자로 주어진 타입으로부터 객체를 만들어 낼 수 있지만, Generic에서는 불가능합니다.
- Generic Class로 만든 모든 객체는 전부 동등한 타입이지만, Template는 다른 타입 인자 사용 시 서로 다른 타입의 객체입니다.
- Generic은 타입 인자를 특정한 타입이 되도록 제한할 수 있습니다.
- Generic은 정적 메서드나 변수를 선언하는 데 사용할 수 없지만, Template는 가능합니다.
```

<br>

<br>

#### 🗨 Lambda 표현식과 함수형 프로그래밍에 대해 설명하세요.

```
Lambda 표현식이란 메소드를 하나의 식으로 표현하는 것으로, 매개변수와 화살표(->), {몸통} 구조로 이루어집니다.
기존에 익명함수로 작성하던 코드를 줄여 간단하게 작성이 가능하여 가독성이 좋고 병렬 프로그래밍에 용이합니다.

자바의 람다 표현식은 함수형 인터페이스로만 사용 가능합니다.
Java 8부터 Lambda식이 도입되었고 Stream이라는 API가 추가되었습니다.
함수형 인터페이스란 1개의 추상 메소드를 갖는 인터페이스를 말합니다.
인터페이스 검증과 유지보수를 위해 @FunctionalInterface 어노테이션을 사용합니다.

함수형 프로그래밍이란 함수형 프로그래밍이란 함수를 1급 객체로 사용하여 계산을 수학적 함수의 조합으로 생각하는 방식입니다.
대용량의 데이터를 빠르고 효율적으로 처리하기 위해서 멀티코어를 활용하는 병렬처리 프로그래밍 도입이 필요해져 함수형 프로그래밍이 필연적으로 선택되었습니다.
1급 객체가 될 수 있는 조건은 아래와 같습니다.
- 변수나 데이터 구조 안에 담을 수 있는 객체
- 함수의 파라미터로 전달 가능
- 반환값으로 사용 가능
- 할당에 사용된 이름과 관계없이 고유한 구별 가능
- 동적으로 프로퍼티 할당 가능
```

<br>

#### 🗨 Collection과 Stream의 차이에 대해 설명하세요.

```
💡 Collection
모든 값을 메모리에 저장하는 자료구조로, 외부 반복을 통해 사용자가 작업 반복 작업을 거쳐 요소를 가져올 수 있습니다. (for-each문)
Collection에 추가하기 전에 미리 계산이 완료되어 있어야 합니다.
외부 반복은 명시적으로 Collection 항목을 하나씩 가져와서 처리해야 하기 때문에 최적화에는 불리합니다.
Collection에서 병렬성을 이용하려면 직접 synchronized 를 통해 관리해야 합니다.


💡 Stream
Stream이란 선언형으로 데이터 Collection을 반복적으로 처리할 수 있는 API입니다.
Lambda식을 지원하며 중간 연산(filter, map...)과 최종연산(foreach, count, collect...)이 있습니다.
요청할 때만 요소를 계산하는 방식으로, 내부 반복을 사용하므로 추출 요소만 선언해주면 알아서 반복 처리를 진행하게 됩니다.
내부 반복은 병렬 처리를 통해 최적화된 순서로 처리해주기 때문에 성능이 더 좋습니다.
스트림에 요소를 추가, 제거하는 작업은 불가능합니다.

🎈 Collection은 음악 파일을 저장하여 재생하는 플레이어라면, Stream은 필요할 때 검색해서 듣는 스트리밍 서비스라고 생각하면 쉽습니다.
```

<br>

#### 🗨 Java 직렬화에 대해 설명하세요.

```
직렬화란 자바 시스템 내부에서 사용되는 객체 또는 데이터를 외부의 자바 시스템에도 사용할 수 있도록 byte 형태로 데이터를 변환하는 기술입니다.
각 PC는 OS마다 서로 다른 가상 메모리 주소 공간을 갖기 때문에 Reference Type의 데이터들은 인스턴스를 전달 할 수 없습니다.
따라서 이런 문제를 해결하기 위해 주소값이 아닌 Byte 형태로 직렬화된 객체 데이터를 전달해야 합니다.

직렬화된 데이터들은 모두 Primitive Type이 되고, 이는 파일 저장이나 네트워크 전송 시 파싱이 가능한 유의미한 데이터가 됩니다.
따라서 전송 및 저장이 가능한 데이터로 만들어주는 것이 바로 직렬화입니다.

Java에서 java.io.Serializable 인터페이스의 구현으로 직렬화를 할 수 있습니다.
ObjectOutputStream을 통해 직렬화하여 Byte로 변환된 값을 저장합니다.
또한 serialVersionUID를 직접 설정해주는 것이 좋은데, 클래스 멤버 변수가 변경되면 serialVersionUID 값 또한 변경되기 때문에 역직렬화 시 Exception이 발생을 방지하기 위해서입니다.
```

<br>

#### 🗨 Java의 역직렬화에 대해 설명하세요.

```
역직렬화란 직렬화된 데이터를 받는 쪽에서 다시 객체 데이터로 변환하기 위한 작업을 말합니다.
직렬화된 바이트 형태의 데이터를 객체로 변환해서 JVM으로 상주시키는 형태의 기술입니다.
직렬화 대상이 된 객체의 클래스가 class path에 존재해야 하고 import되어 있어야 합니다.
자바 직렬화 대상 객체와 동일한 serialVersionUID를 가지고 있어야 합니다.

ObjectOutputStream으로 Byte의 값을 다시 객체에 저장하여 역직렬화를 진행합니다.
```

<br>

#### 🗨 C, C++과 달리 Java에서 객체를 해제하지 않아도 되는 이유에 대해 설명하세요.

```
Java는 C, C++ 언어와 달리 개발자가 명시적으로 객체를 해제할 필요가 없습니다.
Java에서는 JVM(Java Virtual Machine)이 구성된 JRE(Java Runtime Environment)가 제공됩니다.
JVM에서 Garbage Collection을 수행하여 사용하지 않는 객체를 메모리에서 삭제하는 작업을 하게 됩니다.

GC 메모리 해제 과정은 다음과 같습니다.
1. Marking: 프로세스는 마킹을 호출하여 메모리가 사용되는지 아닌지 찾아냅니다. 모든 오브젝트가 스캔되기 때문에 많은 시간이 소모됩니다.
2. Mormal Deletion: 참조되지 않는 객체를 제거하고 메모리를 반환합니다. 메모리 Allocator는 반환되어 비어진 블럭의 참조 위치를 저장해 두었다가 새로운 오브젝트가 선언되면 할당되도록 합니다.
3. Compacting: 퍼포먼스 향상을 위해 참조되지 않는 객체를 제거하고 남은 객체들을 묶음으로서 새로운 메모리 할당 시 더 쉽게 빠르게 진행될 수 있도록 합니다.
```

<br>

#### 🗨 일반적인 Garbage Collection의 메모리 구조에 대해 설명하세요.

```
1. Young Generation 영역
   새롭게 생성한 객체가 위치하는 곳으로 많은 객체가 생성되었다가 사라지는 영역입니다.
   이 영역에서 객체가 사라질 때 Minor GC가 발생한다고 말합니다.
2. Old Generation 영역
   접근 불가능 상태로 되지 않고 Young 영역에서 살아남은 객체가 여기로 복사됩니다.
   Young 영역보다 크게 할당하며 크기가 큰 만큼 GC는 적게 발생합니다.
   이 영역에서 객체가 사라질 때 Major GC 또는 Full GC가 발생한다고 말합니다.
3. Permanent 영역
   Methods Area라고도 하며, JVM이 클래스들과 메소드들을 설명하기 위해 필요한 메타 데이터들을 포함하는 영역입니다.
   JDK8부터는 Meta Space로 교체됩니다.
```

<br>

#### 🗨 Generational Gabage Collection 과정에 대해 설명하세요.

```
1. 새로운 객체가 들어오면 Eden Space에 할당합니다.
2. Eden Space가 가득차면 Minor Garbage Collection이 시작됩니다.
3. 참조중인 객체는 Survivor1 영역으로, 비 참조 객체는 Eden Spacerk Clear될 때 반환됩니다.
4. 다음 Minor GC 때 참조 객체는 Survivor2 영역으로 이동합니다. 참조 객체들이 모두 Survivor2 영역으로 이동하게 되면 Eden Space와 Survivor1 영역은 Clear 됩니다. 주의할 점은 다른 age를 가진 객체들을 한 공간에 가지게 되었다는 것입니다.
5. 다음 Minor GC 에서는 참조 객체들이 Survivor1 영역으로 이동합니다. 이렇게 계속 두 공간을 번갈아가며 사용합니다.
6. Minor GC 후 Survivor 영역이 가득차거나 또는 객체들이 일정한 age threshold를 넘게 되면 Old 영역으로 Promition 됩니다.
7. Major Gsms Old Generation에서 실행 후 Clear 되고 공간이 Compact 됩니다.
```

<br>

#### 🗨 G1 GC에 대해 설명하세요.

```
Java 9 이상의 버전에서 default GC로, 현재 GC 중 stop-the-world의 시간이 제일 짧습니다.
CMS GC 를 개선하여 만든 GC로 다른 GC와 다르게 전체 힙 공간을 체스판처럼 `Region` 이라는 영역으로 나누어 관리합니다.

전체 Heap에 대해서 탐색하지 않고 부분적으로 Region 단위로 탐색하여, 각각의 Region에만 GC가 발생합니다.
Young과 Old 영역의 구분이 없으며, 영역의 참조를 관리할 목적으로 Remember Set을 만들어 사용합니다. (전체 힙의 5% 미만의 크기)
큰 메모리를 가진 멀티 프로세스 시스템에 적합합니다.
```

<br>

#### 🗨 Reflection에 대해 설명하세요.

```

리플렉션이란 구체적인 클래스 타입을 알지 못하더라도 그 클래스의 메서드, 타입, 변수들에 접근할 수 있도록 해주는 자바 API입니다.
컴파일 시간이 아닌 실행 시간에 동적으로 특정 클래스의 정보를 추출할 수 있는 프로그래밍 기법입니다.
리플렉션을 사용하여 가져올 수 있는 정보는 Class, Constructor, Method, Field 가 있습니다.


리플렉션은 동적으로 클래스를 사용해야 할 경우, 즉 작성 시점에는 어떤 클래스를 사용할지 모르지만 런타임 시점에서 가져와 실행하는 경우 필요합니다.
프레임워크나 IDE에서 Spring Annotation, IntelliJ 자동 완성 기능 등의 이런 동적 바인딩을 이용한 기능을 제공합니다.
```

<br>

#### 🗨 Annotation의 역할과 대표적인 Annotation의 몇 가지 예시를 들어주세요.

```java
어노테이션이란 사전적으로는 주석이라는 의미로, 주석처럼 코드에 명시하여 클래스에 특별한 의미를 부여하거나 기능을 주입할 수 있는 기능입니다.
인터페이스를 기반으로 한 문법이며, Built-In Annotation, Meta Annotation, Custom Annotation 세 종류로 구분할 수 있습니다.

Built-In Annotation이란 Java에 내장되어 있는 어노테이션으로 주로 컴파일러에게 유용한 정보를 제공하는 역할을 합니다.
@Override // 메서드 앞에만 붙일 수 있으며 현재 메서드가 Super 클래스의 메소드를 오버라이드한 메소드임을 컴파일러에게 명시합니다. 오타 발생 가능성을 잡아줄 수 있습니다.
@Deprecated // 더 이상 사용하지 않는 메소드를 나타냅니다.
@SupressWarning // 프로그래머의 의도를 컴파일러에게 전달하여 경고를 제거합니다.
@FunctionalInterface // 함수형 인터페이스라는 것을 알리고 검사하는 기능을 제공합니다. 개발자의 실수를 방지할 수 있습니다.

Meta Annotation이란 어노테이션에 사용되는 어노테이션으로 해당 어노테이션의 동작 대상을 결정합니다.
주로 새로운 어노테이션을 정의할 때 사용합니다.
@Target // 어노테이션이 적용가능한 대상을 지정하는데 사용합니다. 여러 개 값을 지정할 때는 {}를 사용합니다.
@Retention // 어노테이션이 유지되는 기간을 지정할 수 있습니다. SOURCE / CLASS / RUNTIME
@Documented // 어노테이션에 대한 정보가 JavaDoc으로 작성한 문서에 포함되도록 할 때 사용하는 어노테이션으로 대부분의 Built-In Annotation에 붙어 있습니다. (@Override, @SuppressWarnings 제외)
@Inherited // 어노테이션이 자손 클래스에도 상속되도록 하는 어노테이션으로, 조상 클래스에 붙이면 자손 클래스도 이 어노테이션이 붙은 것과 같이 인식됩니다.
@Native // JVM이 설치된 OS의 네이티브 메서드에 의해 참조되는 상수 필드에 붙이는 어노테이션입니다. 대표적으로 Object 클래스의 메서드들이 네이티브 메서드에 해당되며, 네이티브 메서드와 자바에 정의된 메서드를 연결하는 것을 JNI(Java Native Interface)라고 합니다.

Custom Annotation
직접 어노테이션 타입을 선언하는 것으로 특별한 종류의 인터페이스입니다.
일반적인 인터페이스 선언과 구분하기 위해 interface 앞에 @를 붙여 사용합니다.
어노테이션 타입은 암묵적으로 java.lang.annotation.Annotation을 확장하기 때문에 extends절을 가질 수 없습니다.
```

<br>

#### 🗨 String vs StringBuffer vs StringBuilder의 차이에 대해 설명하세요.

|                     | String       | StringBuffer | StringBuilder |
| ------------------- | ------------ | ------------ | ------------- |
| 저장 공간           | String pool  | Heap         | Heap          |
| 수정 가능 여부      | X(Immutable) | O(Mutable)   | O(Mutable)    |
| Thread Safe         | O            | O            | X             |
| 동기화 Synchromized | O            | O            | X             |
| 성능                | 빠름         | 느림         | 빠름          |

<br>

#### 🗨 Error와 Exception의 차이에 대해 설명하세요.

```java
오류란 시스템이 종료되어야 할 수준의 상황과 같이 수습할 수 없는 심각한 문제를 의미합니다.
개발자가 미리 예측하여 방지할 수 없습니다.
- StackOverflowError: 호출의 깊이가 깊어지거나 재귀가 지속되어 stack overflow 발생 시 던져지는 오류입니다.
- OutOfMemoryError: JVM이 할당된 메모리의 부족으로 더 이상 객체를 할당할 수 없을 때 던져지는 오류입니다. Garbage Collector에 의해 추가적인 메모리가 확보되지 못하는 상황이기도 합니다.

예외는 개발자가 구현한 로직에서 발생한 실수나 사용자의 영향에 의해 발생합니다.
오류와 달리 개발자가 미리 예측하여 방지 할 수 있기 때문에 상황에 맞는 예외 처리(Exception Handle)을 해야합니다.

예외는 컴파일 시 발생할 수 있는 일반 예외 Exception와 실행 중에 발생하는 런타임 예외 RuntimeException로 구분됩니다.

일반 예외는 소스코드를 .class 파일로 컴파일하는 과정에서 JVM이 던지는 에러로, 대부분 소스코드 자체의 문법적 오류로 인해 발생합니다.
프로그램 자체에서 처리할 수 있는 방법은 없습니다.
일반 예외의 예로는 ClassNotFoundException, IllegalAccessException, NoSuchMethodException등이 있습니다.
- IllegalArgumentException: 메서드가 허가되지 않거나 부적절한 argument를 받았을 경우에 던져지는/던질 수 있는 예외입니다.

런타임 예외는 문법적인 오류가 없어 컴파일 시에는 정상적으로 컴파일됐지만 프로그램을 실행하는 과정에서 발생하는 에러를 말합니다.
이는 개발자가 직접 오류를 확인하여 처리해야 합니다.
런타임 예외의 예로는 NullPointerException, ArithmeticException, IndexOutOfBoundsException 등이 있습니다.<br>
- NullPointerException: 객체가 필요한 경우인데 응용프로그램이 null을 사용하려고 시도할 경우 던져지는/던질 수 있는 예외입니다.
```

<br>

#### 🗨 Java에서 예외 처리 방법에 대해 설명하세요.

```
1. try... catch... finally
예외가 발생했을 때 `try`... `catch`... `finally` 라는 키워드로 예외를 처리하거나 메소드를 호출한 곳으로 던질 수 있습니다. <br>

- `try`: 예외가 발생한 만한 코드가 작성됩니다.
- `catch`: 예외가 발생되었을 때 처리하는 동작을 명시합니다. catch 블록은 여러 개가 있을 수 있습니다.
- `finally`: 예외 발생 유무와 상관 없이 공통으로 수행되어야 할 임시 파일의 삭제 등 뒷정리 코드가 작성됩니다.

2. throws
예외를 바로 처리하지 않고 예외를 던져서 어떤 예외가 발생했는지 알리는 용도로 사용합니다.
throw와 throws 키워드가 사용되는데, throw는 메서드 내에서 예외를 발생시키는 데 사용되고, thorws는 메서드 선언부에서 해당 메서드가 처리하지 않은 예외를 호출자에게 전달함을 나타내기 위해 사용합니다.
```
