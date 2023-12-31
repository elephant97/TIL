# Strategy Pattern(전략패턴)
김영한님 Spring 핵심원리 - 고급편

<br>

### Strategy Pattern(전략패턴)
> 의도: 알고리즘 제품군을 정의하고 각각을 캡슐화하여 상호 교환 가능하게 만들자.    
> 전략을 사용하면 알고리즘을 사용하 는 클라이언트와 독립적으로 알고리즘을 변경할 수 있다.
* 상속이 아닌 위임으로 해결하는 것
* 전략 패턴은 변하지 않는 부분을 `Context` 라는 곳에 두고,      
  변하는 부분을 `Strategy` 라는 인터페이스를 만들고 해당 인터페이스를 구현하도록 해서 문제를 해결
* 스프링의 의존관계 주입에서 사용하는 방식이 전략 패턴 방식
* 선 조립 후 실행 방식
  * 원하는 모양으로 조립해 놓고, Context를 실행하는 방식이다
  * 스프링으로 애플리케이션 개발 시 애플리케이션 로딩 시점에 의존관계 주입을 통해 필요한 의존 관게를 모두 맺어두고 난 다음에 실행 요청을 처리하는 것과 같은 원리

### Strategy Pattern 단점
* Context와 Strategy를 조립한 이후에 전략을 변경하기가 번거러움
* Context를 싱글톤으로 사용할 때에는 동시성 이슈 등 고려할 점이 많다.
* 따라서 전략을 실시간으로 변경해야하면 Context를 하나 더 생성하고, 그 곳에 다른 Strategy를 주입하는 것이 더 나은 선택일 수 있다.
