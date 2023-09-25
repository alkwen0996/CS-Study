# 자료형

자료를 저장하기 위한 메모리 공간으로, 타입에 따라 크기가 달라집니다. <br>
메모리 공간에 값을 할당 후 사용하게 되며, 기본형과 참조형으로 구분할 수 있습니다. <br>

## 기본형 Primitive type

미리 정해진 크기의 메모리 사이즈로 표현하는 방식으로, 변수 자체에 값을 저장하게 됩니다. <br>
총 8가지의 타입으로 나타낼 수 있으며, 메모리의 Stack 영역에 저장됩니다. <br>

- `boolean`: 논리, `true` / `false`
- `byte`: 정수, 1byte
- `short`: 정수, 2byte
- `int`: 정수, 4byte, default type, 20억
- `long`: 정수, 8byte, `l` or `L`
- `float`: 실수, 4byte, `f`
- `double`: 실수, 8byte, default type
- `char`: 문자, 2byte, `A` 65 `a` 97 `0` 48

위 타입들은 비객체 타입으로 null을 가질 수 없습니다. <br>
null을 사용하려면 Wrapper Class를 활용해야 합니다. <br>

## 참조형 Reference type

크기가 미리 정해질 수 없는 데이터의 표현으로, 실제 값을 참조할 수 있는 주소값을 저장하게 됩니다. <br>
아래 그림과 같이 JVM의 Stack 영역에 존재하는 Frame에 일종의 포인터인 참조값을 가지고 있어 인스턴스 핸들링을 합니다. <br>
<img src="./img/reference type.png" width="400"><br>
데이터의 크기가 가변적, 동적이기 때문에 동적으로 관리되는 메모리의 Heap 영역에 저장되고 더 이상 참조하는 변수가 없을 경우에는 Garbage Collector가 메모리를 해제합니다.<br>
java.lang.Object 클래스를 상속하는 모든 클래스들을 의미하며, 클래스, 인터페이스, 배열, 열거 타입이 있습니다. <br>
