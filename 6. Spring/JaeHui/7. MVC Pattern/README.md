# MVC 패턴

## [MVC1](https://chanhuiseok.github.io/posts/spring-3/)

<img src="./img/mvc1.png" width="600"><br>
JSP 페이지에서 View와 Controller 역할 담당하여 로직 처리를 하게 됩니다. <br>
구조는 단순하지만, JSP 내에서 html과 자바 코드가 함께 사용되어 복잡하고 유지보수가 어렵습니다.<br>

## MVC2

<img src="./img/mvc2.png" width="600"><br>
Model, View, Controller로 모듈화된 형태로, JSP는 로직 처리 없이 Client에게 보여지는 View만 담당하게 됩니다.<br>
구조가 복잡하나 유지보수가 용이합니다.<br>

## Spring MVC

- Model: 비지니스 로직를 처리, DB와 상호작용하는 모듈
- View: Client에게 보여지는 화면을 반환하는 모듈
- Controller: 모델과 뷰 사이의 정보 교환, Client 요청이 들어왔을 때, 어떤 로직을 실행할 것인지 제어하는 모듈

<img src="./img/springmvc.png" width="500"><br>

1️⃣ 클라이언트가 서버에 요청을 보내면 DispatcherServlet(Front Controller)에 요청이 전달됩니다.
2️⃣ DispatcherServlet은 요청된 URL을 HandlerMapping에게 전달하고, HandlerMapping은 호출해야 할 Controller 객체를 리턴합니다.
3️⃣DispatcherServlet이 HandlerAdapter 객체에게 요청을 위임하고 HandlerAdapter는 컨트롤러의 메소드를 실행(호출)하여 ModelAndView 객체로 반환합니다.
4️⃣ DispatcherServlet은 ViewResolver를 이용해 View 객체를 얻습니다. ModelAndView 객체의 View이름으로 객체를 찾고, 없다면 생성하여 반환합니다.
5️⃣ DispatcherServlet은 ViewResolver가 리턴한 View객체를 이용해 사용자에게 화면(응답 결과)를 표시합니다.

## DAO, DTO, VO

## DAO(Data Access Object)

DB의 데이터를 조회하거나 조작하는 기능을 전담하도록 만든 객체를 말합니다. <br>
DB에 접근을 하기위한 로직과 비즈니스 로직을 분리하기 위해서 사용합니다. <br>

### DTO(Data Transfer Object)

계층간 데이터 교환을 위한 자바 Bean들을 말합니다. <br>
여기서 말하는 계층은 Controller, View, Business Layer, Persistent Layer 입니다. <br>
일반적인 DTO는 로직을 갖고 있지 않는 순수한 데이터 객체이며, 속성과 그 속성에 접근하기 위한 getter, setter 메소드만 가진 클래스입니다. <br>

### VO(Value Object)

DTO와 동일한 개념이지만 read only 속성을 가지는 객체입니다. <br>
