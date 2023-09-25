# Lambda & Stream

Java 8부터 Lambda식이 도입되었고 Stream이라는 API가 추가되었습니다. <br>
Labmda를 통해 데이터 Collection의 반복 처리가 간단명료해졌고, Stream을 통해 분기 처리 없이 데이터 Collection의 요소를 반복 처리할 수 있게 되었습니다. <br>

## Lambda

Lambda 표현식이란 메소드를 하나의 식으로 표현하는 것으로, 매개변수와 화살표(->), {몸통} 구조로 이루어집니다. <br>
기존에 익명함수로 작성하던 코드를 줄여 간단하게 작성이 가능하여 가독성이 좋고 병렬 프로그래밍에 용이합니다. <br>
하지만 남용하면 오히려 가독성이 떨어질 수 있으며 익명함수 기반이기 때문에 디버깅이 어렵고 재귀 활용이 까다롭습니다. <br>
<br>
자바의 람다 표현식은 함수형 인터페이스로만 사용 가능합니다.<br>
함수형 인터페이스란 1개의 추상 메소드를 갖는 인터페이스를 말합니다. <br>
인터페이스 검증과 유지보수를 위해 @FunctionalInterface 어노테이션을 사용합니다. <br><br>

### [Java에서 기본적으로 제공하는 함수형 인터페이스](https://bcp0109.tistory.com/313)

| 함수형 인터페이스 | Descripter    | Method                  |
| ----------------- | ------------- | ----------------------- |
| Predicate         | T -> boolean  | boolean test(T t)       |
| Consumer          | T -> void     | void accept(T t)        |
| Supplier          | () -> T       | T get()                 |
| Function<T, R>    | T -> R        | R apply(T t)            |
| Comparator        | (T, T) -> int | int compare(T o1, T o2) |
| Runnable          | () -> void    | void run()              |
| Callable          | () -> T       | V call()                |

```
💡 명령형 프로그래밍: 애플리케이션의 상태와 상태를 변경시키는 구문의 관심에서 연산을 설명하는 방식으로 어떻게 할 것인지 표현합니다.
      ├─ 절차 지향 프로그래밍
      └─ 객체 지향 프로그래밍

💡 선언형 프로그래밍: 무엇을 할 것인지 표현하는 방식입니다.
      └─ 함수형 프로그래밍
```

```
✅ 함수형 프로그래밍
하드웨어 발전과 함께 소프트웨어 패러다임은 Text 기반의 절차적 프로그래밍 -> GUI 기반 객체 지향 프로그래밍 -> 멀티코어 기반 함수형 프로그래밍으로 변화해왔습니다.
대용량의 데이터를 빠르고 효율적으로 처리하기 위해서 멀티코어를 활용하는 병렬처리 프로그래밍 도입이 필요해져 함수형 프로그래밍이 필연적으로 선택되었습니다.

함수형 프로그래밍이란 함수를 1급 객체로 사용하여 계산을 수학적 함수의 조합으로 생각하는 방식입니다.
1급 객체가 될 수 있는 조건은 아래와 같습니다.
- 변수나 데이터 구조 안에 담을 수 있는 객체
- 함수의 파라미터로 전달 가능
- 반환값으로 사용 가능
- 할당에 사용된 이름과 관계없이 고유한 구별 가능
- 동적으로 프로퍼티 할당 가능

애플리케이션의 상태는 같은 입력이 주어지면 항상 같은 출력을 반환하는 순수 함수를 통해 전달합니다.
또 명령형 흐름 제어보다 새로운 함수를 만들거나 계산하기 위해 둘 이상의 함수를 조합하여 합성 함수를 만들어 사용합니다. ex) 메소드 체이닝
```

## Stream

Stream이란 선언형으로 데이터 Collection을 반복적으로 처리할 수 있는 API입니다. <br>
Lambda식을 지원하며 중간 연산(filter, map...)과 최종연산(foreach, count, collect...)이 있습니다.<br>
여러 연산을 조립해서 사용할 수 있으며, 병렬로 처리하기 때문에 성능이 좋습니다. <br>

```java
// Java 8 이전
Iterator<String> iter = items.iterator();
while(iter.hasNext()) {
	if(iter.next()!=null){
		System.out.println(iter.next());
	}
}
// Java 8 이후
Stream<String> stream = list.stream();
stream.filter(item->item!=null).forEach(item -> System.out.println(item));
```

분할이 잘 이루어질 수 있는 데이터 구조이거나, 연산 작업이 독립적이면서 CPU 사용률이 높은 작업에 적합합니다. <br>
하지만 Parallel()은 공유된 thread pool을 사용하기 때문에 [성능 장애](https://m.blog.naver.com/tmondev/220945933678)를 일으킬 수 있어서 주의 깊게 사용해야 합니다. <br>

```java
✅ Collection vs Stream
💡 Collection
모든 값을 메모리에 저장하는 자료구조로, 외부 반복을 통해 사용자가 작업 반복 작업을 거쳐 요소를 가져올 수 있습니다. (for-each문)
Collection에 추가하기 전에 미리 계산이 완료되어 있어야 합니다.
외부 반복은 명시적으로 Collection 항목을 하나씩 가져와서 처리해야 하기 때문에 최적화에는 불리합니다.
Collection에서 병렬성을 이용하려면 직접 synchronized 를 통해 관리해야 합니다.


💡 Stream
요청할 때만 요소를 계산하는 방식으로, 내부 반복을 사용하므로 추출 요소만 선언해주면 알아서 반복 처리를 진행하게 됩니다.
내부 반복은 병렬 처리를 통해 최적화된 순서로 처리해주기 때문에 성능이 더 좋습니다.
스트림에 요소를 추가, 제거하는 작업은 불가능합니다.

🎈 Collection은 음악 파일을 저장하여 재생하는 플레이어라면, Stream은 필요할 때 검색해서 듣는 스트리밍 서비스라고 생각하면 쉽습니다.
```

### 중간 연산

파이프라이닝이 가능한 연산으로 스트림을 반환합니다. <br>

```java
filter(Predicate) // Predicate를 인자로 받아 true인 요소를 포함한 스트림 반환
distinct() // 중복 필터링
limit(n) // 주어진 사이즈 이하 크기를 갖는 스트림 반환
skip(n) // 처음 요소 n개 제외한 스트림 반환
map(Function) // 매핑 함수의 result로 구성된 스트림 반환
flatMap() // 스트림의 콘텐츠로 매핑함. map과 달리 평면화된 스트림 반환
```

### 최종 연산

스트림을 닫는 연산으로 중간 연산 값을 한꺼번에 처리합니다. <br>

```java
(boolean) allMatch(Predicate) // 모든 스트림 요소가 Predicate와 일치하는지 검사
(boolean) anyMatch(Predicate) // 하나라도 일치하는 요소가 있는지 검사
(boolean) noneMatch(Predicate) // 매치되는 요소가 없는지 검사
(Optional) findAny() // 현재 스트림에서 임의의 요소 반환
(Optional) findFirst() // 스트림의 첫번째 요소
reduce() // 모든 스트림 요소를 처리해 값을 도출. 두 개의 인자를 가짐
collect() // 스트림을 reduce하여 list, map, 정수 형식 컬렉션을 만듬
(void) forEach() // 스트림 각 요소를 소비하며 람다 적용
(Long) count // 스트림 요소 개수 반환
```
