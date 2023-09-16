# Filter와 Interceptor
<details>
<summary><h3>📑목차</h3></summary>
<div markdown="1">

- [빌드(Build)](#빌드build)

</div>
</details>
<br>

## 필터
- J2EE 표준 스펙 기능
- 디스패처 서블릿에 요청 전달되기 전후에 URL 패턴에 맞는 모든 요청에 대한 부가작업 처리
- 디스패처 서블릿을 스프링의 가장 앞단에 존재하는 프론트 컨트롤러이므로 필터는 스프링 범위 밖에서 처리
- 즉, 웹 컨테이너에 의해 관리 (스프링 빈으로 등록은 됨)


## 필터 추가
- `javax.servlet`의 `Filter` 인터페이스 구현
    - `init()`, `doFilter()`, `destroy()`

#### init()
필터 객체 초기화하고 서비스에 추가하기 위한 메서드이다. 웹 컨테이너가 한번만 init() 메서드를 호출하여 필터 객체를 초기화하면 이후 요청들은 doFilter()를 통해 처리된다.

#### doFilter()
URL 패턴에 맞는 모든 HTTP 요청이 디스패처 서블릿으로 전달되기 전에 웹 컨테이너에 의해 실행되는 메서드이다. `FilterChain`이 파라미터로 존재하는데, `FilterChain`의 `doFilter`를 통해 다음 대상으로 요청을 전달할 수 있음

#### destroy()
필터 객체를 서비스에서 제거하고 사용하는 자원을 반환하기 위한 메서드이다. 