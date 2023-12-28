# DispatcherServlet 
스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술

<br>

### DispatcherServlet 
* `org.springframework.web.servlet.DispatcherServlet`
* 스프링 MVC도 프론트 컨트롤러 패턴으로 구현되어 있다.
* 스프링 MVC의 프론트 컨트롤러가 바로 디스패처 서블릿(DispatcherServlet)이다.
* 디스패처 서블릿이 바로 스프링 MVC의 핵심이다.
* **DispatcherServlet 서블릿 등록**
* `DispatcherServlet` 도 부모 클래스에서 `HttpServlet` 을 상속 받아서 사용하고, 서블릿으로 동작한다.
  * DispatcherServlet->FrameworkServlet->HttpServletBean->HttpServlet
* 스프링 부트는 `DispatcherServlet` 을 서블릿으로 자동으로 등록하면서 **모든 경로**( `urlPatterns="/"` )에 대해서 매핑한다.
* 참고: 더 자세한 경로가 우선순위가 높다. 그래서 기존에 등록한 서블릿도 함께 동작한다.

### DispatcherServlet
