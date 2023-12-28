# HTTP요청 파라미터
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
