## Optional

---

### Optional 이란?

`Optional` 은 `null` 이 될 가능성이 있는 객체를 감싸서 `NPE(NullPointerException)` 를 방지할 수 있도록 `자바8`버전에서 도입된 `Wrapper클래스` 이다. `Optional` 클래스는 내부적으로 `value` 변수에 값을 저장하고 메서드를 통해 값에 접근하기 때문에 `NPE` 를 방지할 수 있다. 또한, `Optional` 을 사용하면 코드에 명시적으로 `null` 이라는 것을 표현할 수 있으며 빈 값에 대한 처리를 강제할 수 있어 프로그램을 안전하게 구현할 수 있다는 특징이 있다.

<br>

### Optional 사용의 장점

- `NPE(NullPointerException)` 를 발생시킬 수 있는 `null` 을 직접 다루지 않아도 된다.
- 불필요한 `null` 확인을 위한 방어로직을 작성하지 않아 가독성을 향상시킬 수 있다.
- 명시적으로 해당 변수가 `null` 일 가능성이 있다는 것을 표현할 수 있다.

<br>

### Optional 사용시 주의할 점

- [`필드`나 `메서드 파라미터` 등에 사용하지 마라]
- 검증하지 않고 `get()` 하지 마라
- 단순 `null` 확인을 위한 목적으로 사용하지 마라
- `Optional` 에서 제공하는 메서드를 적극 활용해라
- 배열이나 컬렉션을 감싸지 마라
- `of` 와 `ofNullable()` 을 구분해라
- 반환타입으로만 사용하라
- 값이 없을 때 `Optiona.orElse()` 로 기본 값을 반환하라
- 동등성 비교를 위해 객체를 꺼내지 마라

<br>

### [Reference]

[Optional](https://catsbi.oopy.io/81ee5bdc-6825-46f8-b1d2-c608ab2d6465)
