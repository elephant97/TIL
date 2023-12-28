# HTTP 파라미터
스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술

<br>

## HTTP 요청 데이터 조회

### 클라이언트에서 서버로 요청 데이터를 전달할 때 사용하는 주요 방법 3가지
* **GET - 쿼리 파라미터**
  * /url**?username=hello&age=20**
  * 메시지 바디 없이, URL의 쿼리 파라미터에 데이터를 포함해서 전달
  * 예) 검색, 필터, 페이징등에서 많이 사용하는 방식
* **POST - HTML Form**
  * content-type: application/x-www-form-urlencoded
  * 메시지 바디에 쿼리 파리미터 형식으로 전달 username=hello&age=20
  * 예) 회원 가입, 상품 주문, HTML Form 사용
* **HTTP message body**에 데이터를 직접 담아서 요청
  * HTTP API에서 주로 사용, JSON, XML, TEXT
  * 데이터 형식은 주로 JSON 사용
  * POST, PUT, PATCH

### 요청 파라미터 - 쿼리 파라미터, HTML Form
> `HttpServletRequest` 의 `request.getParameter()` 를 사용하면 다음 두가지 요청 파라미터를 조회할 수 있다.
* **GET, 쿼리 파라미터 전송**
  ```
  http://localhost:8080/request-param?username=hello&age=20
  ```
* **POST, HTML Form 전송**
  ```
  POST /request-param ...
  content-type: application/x-www-form-urlencoded
  username=hello&age=20
  ```
* GET 쿼리 파리미터 전송 방식이든, POST HTML Form 전송 방식이든 둘다 형식이 같으므로 구분없이 조회할 수 있 다.
* 간단히 **요청 파라미터(request parameter) 조회**라 한다.

### HTTP 응답 - 정적 리소스, 뷰 템플릿
* 정적 리소스
  * 예) 웹 브라우저에 정적인 HTML, css, js를 제공할 때는, **정적 리소스**를 사용한다.
* 뷰 템플릿 사용
  * 예) 웹 브라우저에 동적인 HTML을 제공할 때는 뷰 템플릿을 사용한다.
* HTTP 메시지 사용
   * HTTP API를 제공하는 경우에는 HTML이 아니라 데이터를 전달해야 하므로, HTTP 메시지 바디에 JSON 같은 형식으로 데이터를 실어 보낸다.

### 정적리소스
* 스프링 부트는 클래스패스의 다음 디렉토리에 있는 정적 리소스를 제공한다.
   * `/static` , `/public` , `/resources` ,`/META-INF/resources`
   * `src/main/resources` 는 리소스를 보관하는 곳이고, 또 클래스패스의 시작 경로이다.
   * 따라서 다음 디렉토리에 리소스를 넣어두면 스프링 부트가 정적 리소스로 서비스를 제공한다.

### 뷰 템플릿
* 뷰 템플릿을 거쳐서 HTML이 생성되고, 뷰가 응답을 만들어서 전달한다.
* 일반적으로 HTML을 동적으로 생성하는 용도로 사용하지만, 다른 것들도 가능하다. 뷰 템플릿이 만들 수 있는 것이라 면 뭐든지 가능하다.
* 스프링 부트는 기본 뷰 템플릿 경로를 제공한다.
  * `src/main/resources/templates`

### HTTP 메세지 컨버터
>  응답의 경우 클라이언트의 HTTP Accept 해더와 서버의 컨트롤러 반환 타입 정보 둘을 조합해서 `HttpMessageConverter` 가 선택된다
* `@ResponseBody` 를 사용
  * HTTP의 BODY에 문자 내용을 직접 반환
  * `viewResolver` 대신에 `HttpMessageConverter` 가 동작
  * 기본 문자처리: `StringHttpMessageConverter`
  * 기본 객체처리: `MappingJackson2HttpMessageConverter`
  * byte 처리 등등 기타 여러 HttpMessageConverter가 기본으로 등록되어 있음
