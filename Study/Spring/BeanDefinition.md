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
