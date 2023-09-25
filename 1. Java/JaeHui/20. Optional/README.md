# [Optional](http://www.tcpschool.com/java/java_stream_optional#google_vignette)

Java8에서 도입된 클래스로 NullPointerException을 방지할 수 있도록 도와주는 Wrapper 클래스입니다. <br>
모든 타입의 참조 변수를 저장할 수 있고, 값이 null이더라도 바로 NPE가 발생하지 않습니다. <br>

## 객체 생성

`of()` 메소드나 `ofNullable()` 메소드를 사용하여 Optional 객체를 생성합니다. <br>
null이 될 가능성이 있다면 `ofNullable()` 메소드를 사용해야 비어 있는 Optional 객체를 반환하기 때문에 NullPointerException이 발생하지 않습니다. <br>

```java
Optional<String> opt = Optional.ofNullable("자바 Optional 객체"); // 객체 생성
if(opt.isPresent()) { // null 체크
    System.out.println(opt.get()); // 객체 접근
}
```

`get()`으로 객체에 접근할 때 저장된 값이 null이면 NoSuchElementException 예외가 발생할 수 있기 때문에 `isPresent()` 메소드를 사용하여 null 체크를 먼저 해야 합니다. <br>

| 메소드                                                                       | 설명                                                                                                                         |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| static <T> Optional<T> empty()                                               | 아무런 값도 가지지 않는 비어있는 Optional 객체를 반환함.                                                                     |
| T get()                                                                      | Optional 객체에 저장된 값을 반환함.                                                                                          |
| boolean isPresent()                                                          | 저장된 값이 존재하면 true를 반환하고, 값이 존재하지 않으면 false를 반환함.                                                   |
| static <T> Optional<T> of(T value)                                           | null이 아닌 명시된 값을 가지는 Optional 객체를 반환함.                                                                       |
| static <T> Optional<T> ofNullable(T value)                                   | 명시된 값이 null이 아니면 명시된 값을 가지는 Optional 객체를 반환하며, 명시된 값이 null이면 비어있는 Optional 객체를 반환함. |
| T orElse(T other)                                                            | 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 값을 반환함.                                       |
| T orElseGet(Supplier<? extends T> other)                                     | 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 람다 표현식의 결괏값을 반환함.                     |
| <X extends Throwable> T orElseThrow(Supplier<? extends X> exceptionSupplier) | 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 예외를 발생시킴.                                   |
