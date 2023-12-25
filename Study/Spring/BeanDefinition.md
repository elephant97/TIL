# BeanDefinition - 스프링 빈 설정 메타 정보
김영한님 Spring 핵심원리 - 기본편

<br>

### 스프링 빈 설정 메타 정보
* 스프링은 BeanDefinition이라는 추상화가 있다
* 역할과 구현을 개념적으로 나눈 것이다.
  * XML을 읽어서 BeanDefinition을 만들면 된다
  * 자바 코드를 읽어서 BeanDefinition을 만들면 된다
  * 스프링 컨테이너는 자바 코드인지, XML인지 몰라도 된다 오직 BeanDefinition만 알면 된다
* BeanDefinition을 빈 설정 메타정보라 한다.
* 스프링 컨테이너는 이 메타정보를 기반으로 스프링 빈을 생성한다.
* `AnotationConfigApplicationContext`는 `AnnotationBeanDefinitionReader`를 사용해서     
  `AppCnfig.class`를 읽고 `BeanDefinition`을 생성한다.
* `GenericXmlApplicationContext`는  `XmlBeanDefinitionReader`를 사용해서 `appConfig.xml`설정 정보를     
  읽고 `BeanDefinition`을 생성한다.
* 새로운 형식의 설정 정보가 출력되면 XxxBeanDefinitionReader를 만들어서 `BeanDefinition`을 생성하면 된다.

### BeanDefinition 살펴보기
* BeanDefinition 정보
 * BeanClassName
   * 생성할 빈의 클래스 명(자바 설정 처럼 팩토리 역할의 빈을 사용하면 없음) factoryBeanName: 팩토리 역할의 빈을 사용할 경우 이름
   * 예) appConfig
 * factoryMethodName
   * 빈을 생성할 팩토리 메서드 지정, 예) memberService
 * Scope
   * 싱글톤(기본값)
 * lazyInit
   * 스프링 컨테이너를 생성할 때 빈을 생성하는 것이 아니라, 실제 빈을 사용할 때 까지 최대한 생성을 지연 처리 하는지 여부
 * InitMethodName
   * 빈을 생성하고, 의존관계를 적용한 뒤에 호출되는 초기화 메서드 명 DestroyMethodName: 빈의 생명주기가 끝나서 제거하기 직전에 호출되는 메서드 명
 * Constructor arguments, Properties
   * 의존관계 주입에서 사용한다. (자바 설정 처럼 팩토리 역할의 빈을 사용 하면 없음)
