# String vs StringBuffer vs StringBuilder

|                     | String       | StringBuffer | StringBuilder |
| ------------------- | ------------ | ------------ | ------------- |
| 저장 공간           | String pool  | Heap         | Heap          |
| 수정 가능 여부      | X(Immutable) | O(Mutable)   | O(Mutable)    |
| Thread Safe         | O            | O            | X             |
| 동기화 Synchromized | O            | O            | X             |
| 성능                | 빠름         | 느림         | 빠름          |

## [String](https://ifuwanna.tistory.com/221)

String 객체는 한번 값이 할당되면 그 공간은 변하지 않습니다. <br>
`+` 연산자 또는 `concat` 메소드를 통해 다른 문자열을 추가하더라도 기존 문자열에 붙이는 것이 아니라,<br>
새로운 String 객체를 만든 후 새 String 객체에 연결된 문자열을 저장하고 그 객체를 참조하도록 합니다. <br>
즉 String 클래스 객체는 Heap 메모리 영역에 생성되고 한번 생성된 객체의 내부 내용을 변화시킬 수 없습니다. <br>
주로 문자열 연산이 적고 멀티스레드 환경일 경우 사용합니다. <br>

## StringBuffer

주로 문자열 연산이 많고 멀티스레드 환경일 경우 사용합니다. <br>
StringBuffer는 가변성을 가지기 때문에 `append()`, `delete()`와 같은 API를 이용하여 동일 객체 내 문자열을 변경하는 것이 가능합니다. <br>
또한 동기화를 지원하여 멀티스레드 환경에서 안전(thread-safe)하다는 장점을 가지고 있습니다. <br>

## StringBuilder

주로 문자열 연산이 많고 단일 스레드이거나 동기화를 고려하지 않아도 되는 경우 사용합니다. <br>
StringBuffer와 동일하게 가변성을 갖지만, 동기화를 지원하지 않습니다. <br>
따라서 멀티스레드 환경에서 사용하는 것은 적합하지 않지만, 단일 스레드에서는 StringBuffer보다 성능이 좋습니다. <br>
