# Filter와 Interceptor
<details>
<summary><h3>📑목차</h3></summary>
<div markdown="1">

- [필터](#필터)
    - [필터 추가](#필터-추가)
        - [init()](#init)
        - [doFilter()](#dofilter)
        - [destroy()](#destroy)
- [인터셉터](#인터셉터)
    - [인터셉터 추가](#인터셉터-추가)
        - [preHandle()](#prehandle)
        - [postHandle()](#posthandle)
        - [afterCompletion()](#aftercompletion)
- [필터와 인터셉터 비교](#필터와-인터셉터-비교)
    - [웹 컨테이너와 스프링 컨테이너](#웹-컨테이너서블릿-컨테이너와-스프링-컨테이너)
    - [Request/Response 객체 조작](#request--response-객체-조작)

</div>
</details>
<br>

공통적으로 **여러 작업을 처리하여 중복된 코드를 제거**할 수 있도록 Spring은 `필터`, `인터셉터`, `AOP`의 기능을 제공해준다. 이 3가지 기능은 모두 어떤 행동을 하기 전에 먼저 실행되거나 실행 후 추가적인 행동을 할 떄 사용되는 기능들이다. 

<p align="center">
    <img src="./img/필터와 인터셉터.png" width="500px">
</p>

## 필터
- J2EE 표준 스펙 기능 (Java가 제공하는 기술)
- 디스패처 서블릿에 요청 전달되기 전후에 URL 패턴에 맞는 모든 요청에 대한 부가작업 처리
- 디스패처 서블릿을 스프링의 가장 앞단에 존재하는 프론트 컨트롤러이므로 필터는 스프링 범위 밖에서 처리
- 즉, 웹 컨테이너에 의해 관리 (스프링 빈으로 등록은 됨)

<br>

### 필터 추가
- `javax.servlet`의 `Filter` 인터페이스 구현
    - `init()`, `doFilter()`, `destroy()`

```java
public interface Filter {

    public default void init(FilterConfig filterConfig) throws ServletException {}
    
    public void doFilter(ServletRequest request, ServletResponse response,
            FilterChain chain) throws IOException, ServletException;
            
    public default void destroy() {}

}
```
<br>

### init()
**필터 객체 초기화하고 서비스에 추가**하기 위한 메서드이다. **웹 컨테이너**가 한번만 `init()` 메서드를 호출하여 필터 객체를 초기화하면 **이후 요청들은 `doFilter()`를 통해 처리**된다.

<br>

### doFilter()
URL 패턴에 맞는 모든 HTTP 요청이 디스패처 서블릿으로 전달되기 전에 웹 컨테이너에 의해 실행되는 메서드이다. `FilterChain`이 파라미터로 존재하는데, `FilterChain`의 `doFilter`를 통해 다음 대상으로 요청을 전달할 수 있음

<br>

### destroy()
**필터 객체를 서비스에서 제거하고 사용하는 자원을 반환**하기 위한 메서드이다. 웹 컨테이너에 의해 한 번 호출된다. 

<br>

## 인터셉터
- Spring이 제공하는 기술
- **디스패처 서블릿이 컨트롤러를 호출하기 전후**에 요청과 응답을 참조하거나 가공할 수 있는 기능 제공
- 스프링 컨테이너에서 동작
- 디스패처 서블릿이 핸들러 매핑을 통해 적절한 컨트롤러를 찾도록 요청 → 결과로 실행 체인(`HandlerExcutionChain`) 돌려줌 → 실행 체인에 **인터셉터가 등록**되어 있으면 순차적으로 인터셉터 거쳐 컨트롤러 실행
- 인터셉터가 컨트롤러로 요청을 위임하는 것은 아님 (그림은 순서를 도식화한 것)

### 인터셉터 추가
- `org.springframework.web.servlet`의 `HandlerInterceptor` 인터페이스 구현
    - `preHandle()`, `postHandle()`, `afterCompletion()`

```java
public interface HandlerInterceptor 

    default boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler)
	throws Exception {
        return true;
    }
    
    default void postHandle(HttpServletRequest request, HttpServletResponse response,
	Object handler, @Nullable ModelAndView modelAndView) throws Exception {}
        
    default void afterCompletion(HttpServletRequest request, HttpServletResponse response,
	Object handler, @Nullable Exception ex) throws Exception { }
        
}
```
<br>

### preHandle()
**컨트롤러가 호출되기 전에 실행**되는 메서드로 컨트롤러 이전에 처리해야하는 전처리 작업이나 요청 정보를 가공 및 처리하는 경우에 사용한다. 반환 타입은 `true/false`로 `true`이면 다음 단계(다음 인터셉터 또는 컨트롤러) 작업을 진행하지만, `false`이면 작업을 중단하여 이후 작업이 진행되지 않는다.

<br>

### postHandle()
**컨트롤러가 호출된 이후에 실행**되는 메서드로 컨트롤러 이후에 처리해야 하는 후처리 작업이 있을 때 사용한다. 해당 메서드에는 컨트롤러가 반환하는 `ModelAndView` 타입의 정보가 제공되는데 RestAPI 기반의 컨트롤러(@RestController)가 많이 사용되면서 적게 사용된다. 또한 컨트롤러 하위 계층에서 **예외가 발생하면 postHandle()은 호출되지 않는다.** 

<br>

### afterCompletion()
**뷰 페이지가 렌더링 되고 난 후 실행되는 메서드.** 모든 뷰에서 최종 결과를 생성하는 일을 포함해 모든 작업이 완료된 후 실행되는 메서드로 요청 처리 중 사용한 리소스를 반환할 때 주로 사용한다. postHandle()과 달리 컨트롤러 하위 계층에서 **예외가 발생해도 afterCompletion은 반드시 호출**된다. 

<br>

## 필터와 인터셉터 비교

#### 웹 컨테이너(서블릿 컨테이너)와 스프링 컨테이너
필터는 서블릿 영역에서 관리되지만, 인터셉터는 스프링 영역에서 관리된다. 따라서 필터는 스프링이 처리해주는 내용들을 적용할 수 없다. 대표적으로 필터는 스프링에 의해 예외처리가 불가하다.  

<br>

#### Request / Response 객체 조작
필터는 서블릿 컨테이너 범위에서 동작되기 때문에 Request와 Response 객체를 조작할 수 있지만 인터셉터는 조작할 수 없다. 

아래의 코드를 통해 확인해보면 필터는 다음 필터를 호출하기 위해 필터 체이닝을 한다. 즉, 다음 필터를 호출시 매개변수로 원하는 Request, Response 객체를 넘겨줄 수 있다.

하지만 인터셉터의 `preHandle()` 코드를 살펴보면 반환값이 boolean 값으로, 여러 인터셉터 목록을 가지고 있을 때 디스패처 서블릿이 for문을 통해 순차척으로 실행시키다 반환값이 false면 요청이 중단된다. 따라서 개발자가 다른 Request, Response 객체를 지정해 넘겨줄 수 없다. 

```java
// 필터
public MyFilter implements Filter {

    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) {
        // 개발자가 다른 request와 response를 넣어줄 수 있음
        chain.doFilter(new MockHttpServletRequest(), new MockHttpServletResponse());       
    }
    
}
```
```java
// 인터셉터
public class MyInterceptor implements HandlerInterceptor {

    default boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) {
        // Request/Response를 교체할 수 없고 boolean 값만 반환할 수 있다.
        return true;
    }

}
```
#### 👉 Filter
- 공통된 보안 및 인증, 인가 작업
- 모든 요청에 대한 로깅 
- 이미지/데이터 압축 및 문자열 인코딩
- Spring과 분리되어야 하는 기능

#### 👉 Interceptor
- 세부적인 보안 및 인증, 인가
- API 호출에 대한 로깅
- 컨트롤러로 넘겨주는 정보 가공

