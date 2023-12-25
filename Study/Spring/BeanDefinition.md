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
