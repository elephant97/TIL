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
  * 스프링 MVC로 인식
* `@Service`
  * 스프링 비즈니스 로직에서 사용
  * 특별한 처리는 하지 않으나, 핵심 비지니스 로직이 있다는 비지니스 계층을 인식하는데 도움이 됨.
* `@Repository`
  * 스프링 데이터 접근 계층에서 사용
  * 스프링 데이터 접근 계층으로 인식하고, 데이터 계층의 예외로 변환해 줌
* `@Configuration`
  * 스프링 설정 정보에서 사용
  * 스프링 설정 정보로 인식하고, 스프링 빈이 싱글톤을 유지하도록 추가 처리함
*어노테이션에는 상속관계가 없으며 특정 어노테이션을 들고있는 것을 인식할 수 있는 것은 자바가 아닌 스프링에서 지원하는 기능*

### 필터
* includeFilters
  * 컴포넌트 스캔 대상을 추가로 지정한다.
* excludeFilters
  * 컴포넌트 스캔에서 제외할 대상을 지정한다.

### FilterType 옵션
* ANNOTATION: 기본값, 애노테이션을 인식해서 동작한다.
  * ex) `org.example.SomeAnnotation`
* ASSIGNABLE_TYPE: 지정한 타입과 자식 타입을 인식해서 동작한다.
  * ex) `org.example.SomeClass`
* ASPECTJ: AspectJ 패턴 사용
  * ex) `org.example..*Service+`
* REGEX: 정규 표현식
  * ex) `org\.example\.Default.*`
* CUSTOM: `TypeFilter` 이라는 인터페이스를 구현해서 처리
  * ex) `org.example.MyTypeFilter`

 ### 중복 등록과 충돌
 * 자동 빈 등록 vs 자동 빈 등록 에서의 충돌
   * 컴포넌트 스캔에 의해 자동으로 스프링 빈이 등록되는데, 그 이름이 같은 경우 스프링은 오류 발생 시킴
     * `ConflictingBeanDefinitionException` 예외 발생
 * 수동 빈 등록 vs 자동 빈 등록 에서의 충돌
   * 수동 빈 등록이 우선권을 가진다. (수동 빈이 자동 빈을 오버라이딩 해버린다.)
   * 수동 빈 등록시 남는 로그**
     ```text
      Overriding bean definition for bean 'memoryMemberRepository' with a different
      definition: replacing
     ```
 *이런 설정이 꼬여서 발생하는 경우를 방어하기 위해 스프링 부터에서는 수동 빈 등록과 자동 빈 등록에서 충돌이 발생하는 경우 오류가 발생하도록 기본 값을 바꿈*
   * 수동 빈 등록, 자동 빈 등록 오류시 스프링 부트 에러
     ```text
       Consider renaming one of the beans or enabling overriding by setting
       spring.main.allow-bean-definition-overriding=true
     ```
