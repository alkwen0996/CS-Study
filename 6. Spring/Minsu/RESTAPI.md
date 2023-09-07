## Restful API

---

### REST 란?

자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 방법을 말한다. 더 구체적으로 말하자면 `REST` 란 `URI` 를 통해 `자원`을 명시하고 `HTTP Method` 를 통해 자원에 대한 `상태`를 `표현`하는 것을 의미한다.

<br>

### REST 구성요소

`REST`는 3가지의 구성요소로 이루어져 있다.

- `자원 ( Resource )` - `URI`
- `행위 ( Verb )` - `HTTP Method`
- `표현 ( Representations )` - `HTTP Message Pay Load`

<br>

### REST 특징

- `Uniform Interface`
- `Stateless`
- `Cacheable`
- `Self-descriptiveness`
- `Clinet-Server 구조`
- `계층형 구조`

<br>

### REST API 란?

`REST`의 원리를 기반으로 서비스의 `API`를 구현한 것을 의미한다.

<br>

### REST API 설계 가이드

- `URI`는 `정보의 자원`을 표현해야 한다. ( 행위에 대한 표현이 들어가서는 안된다. )
- `자원`에 대한 행위는 `HTTP Method ( GET, POST, PUT, PATCH 등 )` 으로 표현해야 한다.

<br>

### REST API 설계시 주의사항

- 슬래시 구분자 ( `/` ) 는 계층 관계를 나타내는 데 사용한다.
- `URI` 마지막 문자로 슬래시 ( `/` ) 를 포함하지 않는다.
- 하이픈 ( `-` ) 은 `URI` 가독성을 높이는데 사용된다. 단, 언더바 ( `_` ) 는 사용하지 않는다.
- 특별한 경우를 제외하고 대문자를 사용하지 않는다.
- `URI` 는 동사보다는 명사를 사용한다.
- 확장자가 포함된 파일 이름을 사용하지 않는다.

<br>

### 기존의 웹 접근 방식과 REST API 방식의 차이점

기존의 웹은 `GET` 과 `POST` 만으로 자원에 대한 `CRUD` 를 처리하며 `URI` 는 `행위`를 표현했다.

하지만, `REST` 를 이용한 방식은 `GET`, `POST`, `PUT` 그리고 `PATCH` 등 여러 `HTTP Method` 를 사용하여 `CRUD`를 처리하며 `URI`는 제어 하려는 `자원`을 나타낸다.

<br>

### 기존 Service 와 REST 방식의 Service 차이점

기존의 `Service Layer` 는 요청에 대한 처리 후 가공된 `Data` 를 이용하여 특정 플랫폼에 적합한 형태의 `View` 로 만들어서 클라이언트에게 반환하는 방식이었다.

하지만, `REST` 를 이용한 `Service Layer` 에서는 `Data` 처리만 한다거나 처리 후 반환될 `Data` 가 있다면 JSON 이나 `XML` 형식으로 `Data` 만 전달한다. 기존의 방식과는 달리 `View`에 대해서 고려하지 않는다.

<br>

### RESTFul 이란?

`REST` 의 원리를 따라는 시스템을 의미한다. `REST API` 를 제공하는 서비스를 `RESTful` 하다고 표현한다. 하지만 `REST` 를 사용했다고 하여 모두가 `RESTful` 한 것은 아니다. `REST API` 의 설계 규칙을 올바르게 지킨 시스템을 RESTful 하다고 말할 수 있으며 모든 `CRUD` 기능을 `POST` 로 처리하는 `API` 혹은 `URI` 규칙을 올바르게 지키지 않은 `API` 는 `REST API`의 설계 규칙을 올바르게 지키지 못한 시스템은 `REST API`를 사용하였지만 `RESTful` 하지 못한 시스템이라고 할 수 있다.

```java
GET /board/delete/1
// 잘못된 URI

GET /board/1
// 수정된 URI
```

위의 두 `URI` 중 첫번째 `URI`와 같은 방식은 `REST`를 제대로 적용하지 못한 `URI`이다. `URI`는 자원을 표현하는데 중점을 두어야 한다. `delete`와 같은 표현이 들어가서는 안된다. 첫 번째의 잘못된 `URI`는 두번째의 `URI`와 같이 수정할 수 있다.

<br>

### **[ Reference ]**

[REST API 제대로 알고 사용하기 : NHN Cloud Meetup](https://meetup.nhncloud.com/posts/92)

[[네트워크] REST API란? REST, RESTful이란?](https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80)

[[간단정리] REST, REST API, RESTful 특징](https://hahahoho5915.tistory.com/54)
