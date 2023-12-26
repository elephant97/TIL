# 컴포넌트 스캔
김영한님 Spring 핵심원리 - 기본편

<br>

### @ComponentScan
* @ComponentScan은 @Component가 붙은 모든 클래스를 스프링 빈으로 등록한다
* 스프링 빈의 기본 이름은 클래스명을 사용하되 맨 앞글자만 소문자를 사용한다
  * 빈 이름 기본 전략
    * MemberServiceImpl 클래스 -> memberServiceImple
  * 빈 이름 직접 지정
    * 스프링 빈의 이름을 직접 지정하고 싶을 시 @Component("membersvc")이런식으로 이름을 부여하면 됨.

### 컴포넌트 탐색 위치와 기본 스캔 대상
* 모든 클래스를 컴포넌트 스캔하면 시간이 오래 소요되기 때문에 필요한 위치부터 탐색하도록 시작 위치 지정 가능
```java
 @ComponentScan(
         basePackages = "hello.core",
}
```
* basePackeges
  * 탐색할 패키지의 시작 위치를 지정.
  * 이 패키지를 포함해서 하위 패키지 모두 탐색
  * 아래와 같이 시작 위치를 지정할 수도 있음
    ```java
    basePackages = {"hello.core", "hello.service"} `
    ```
* basePackageClasses
  * 지정한 클래스의 패키지를 탐색 시작 위치로 지정한다.
* 지정하지 않을 시 @Component가 붙은 설정 정보 클래스의 패키지가 시작위치가 됨
*패키지 위치를 지정하지 않고, 설정 정보 클래스의 위치를 프로젝트 최상단(루트위치)에 두는 것을 권장. 최근 스프링 부트도 이 방법을 기본으로 제공* 

### 컴포넌트 스캔의 기본 대상
> 컴포넌트 스캔은 @Component 뿐만 아니라 다음과 같은 내용도 추가로 대상에 포함
* `@Component`
  * 컴포넌트 스캔에서 사용
* `@Controller`
  * 스프링 MVC 컨트롤러에서 사용
* `@Service`
  * 스프링 비즈니스 로직에서 사용
* `@Repository`
  * 스프링 데이터 접근 계층에서 사용
* `@Configuration`
  * 스프링 설정 정보에서 사용
