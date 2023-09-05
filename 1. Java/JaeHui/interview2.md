## 📝 Interview

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
