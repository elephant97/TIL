# 객체지향5원칙 SOLID 📌
> 객체지향 프로그래밍을 하면서 지켜야하는 5대 원칙으로 SRP(단일책임원칙), OCP(개방-폐쇄 원칙), LSP(리스코프 치환 원칙), ISP(인터페이스 분리원칙),
> DIP(의존 역전 원칙)의 앞글자를 따서 만들어졌다. SOLID 원칙을 철저히 지키면 시간이 지나도 변경이 용이하고, 유지보수와 확장이 쉬운 소프트웨어를 개발하는데
> 도움이 된다.
* **좋은 소프트웨어의 설계에서는 응집도는 높이고, 결합도는 낮추는 것이 바람직함**
* **결합도는 모듈(클래스)간의 상호 의존 정도로서 결합도가 낮으면 모듈 간의 상호 의존성이 줄어들어 객체의 재사용이나 수정, 유지보수 용이**
* **응집도는 하나의 모듈 내부에 존재하는 구성 요소들의 기능적 관련성으로, 응집도가 높은 모듈은 하나의 책임에 집중하고 독립성이 높아져 재사용이나      
  기능의 수정, 유지보수가 용이하다.**
* **SOLID를 잘 녹여낸 소프르웨어는 상대적으로 이해하기 쉽고, 리팩터링과 유지보수가 수월하며, 논리적으로 정연하다.**

### 단일책임의 원칙(SRP, Single Responsibility Principle)
> 모듈이 변경되는 이유가 한가지여야 함. 즉 해당 모듈이 여러 대상 또는 액터들에 대해 책임을 가져서는 안되고, 오직 하나의 액터에 대해서만 책임을 져야한다.
> 여기서 모듈이란 class 또는 class 모음으로 해석할 수 있음
* 역할(책임)을 분리하라는 것이 단일 책임 원칙
* 단일 책임 원칙은 속성, 메서드, 패키지, 모듈, 컴포넌트, 프레임워크 등에도 적용할 수 있는 개념
* 하나의 속성이 여러 의미를 갖는 경우도 단일 책임 원칙을 지키지 못하는 경우이다.
* 단일 책임 원칙과 가장 관계가 깊은 것은 모델링 과정을 담당하는 **추상화**이다.

### 개방 폐쇄 원칙 (OCP, Open-Closed Principle)
> 자신의 확장에 대해 열려있고, 주변의 변화에 대해서는 닫혀있어야 한다.
> 소프트웨어 엔티티(클래스, 모듈, 함수 등)는 확장에 대해서는 열려 있어야 하지만 변경에 대해서는 닫혀 있어야 한다.
  * 확장에 대해 열려있다 : 요구사항이 변경될 때 새로운 동작을 추가하여 애플리케이션의 기능을 확장할 수 있다.
  * 수정에 대해 닫혀있다 : 기존의 코드를 수정하지 않고, 애플리케이션의 동작을 추가하거나 변경할 수 있다.
* 예시
  * 데이터베이스 프로그래밍을 지원하는 라이브러리와 프레임워크에서도 개방 폐쇄 원칙의 예를 볼 수 있음.
    * 데이터베이스라고 하는 주변의 변화에 닫혀있으며, 데이터베이스를 교체한다는 것은 데이터베이스가 자신의 확장에는 열려있다는 것
  * JVM
    * 개발자가 작성한 소스코드는 운영체제의 변화에 닫혀있고, 각 운영체제별 JVM은 확장에 열려있는 구조가 되는 것.
  * 상속 구조
  * 스프링프레임워크
* 개방폐쇄 원칙을 지키며 프로그램을 작성하면 객체 지향 프로그래밍의 가장 큰 장점인 유연성, 재사용성, 유지보수성 등을 얻을 수 있음

### 리스코프 치환 원칙 (LSP, Liskov Substitution Principle)
> 올바른 상속 관계의 특징을 정의하기 위해 발표한 것으로, 하위 타입은 상위 타입을 대체할 수 있어야 한다는 것.
> 즉, 해당 객체를 사용하는 클라이언트는 상위 타입이 하위타입으로 변경되어도, 차이점을 인식하지 못한 채 타입의 퍼블릭 인터페이스를 통해
> 서브클래스를 이용할 수 있어야 한다는 것
* 서브타입은 언제나 자신의 기반 타입으로 교체할 수 있어야 한다.
* 하위 클래스의 인스턴스는 상위형 객체 참조 변수에 대입해 상위 클래스의 인스턴스 역할을 하는데 문제가 없어야 한다.
  * **하위형에서 선행 조건은 강화될 수 없다.**
  * **하위형에서 후행 조건은 약화될 수 없다.**
  * **하위형에서 상위형의 불변 조건은 반드시 유지돼야 한다.**

### 인터페이스 분리 원칙 (ISP, Interface Segregaion Principle)
> 객체가 충분히 높은 응집도의 작은 단위로 설계됐더라도, 목적과 관심이 각기 다른 클라이언트가 있다면 인터페이스를 통해 적절하게 분리하는 것.
> 즉, 클라이언트의 목적과 용도에 적합한 인터페이스만을 제공하는 것
* 클라이언트는 자신이 사용하지 않는 메서드에 의존 관계를 맺으면 안된다.
* 모든 클라이언트가 자신의 관심에 맞는 퍼블릭 인터페이스(외부에서 접근 가능한 메세지)만을 접근하여 불필요한 간섭을 최소화 해야 함
* 기존 클라이언트에 영향을 주지 않은 채로 유연하게 객체의 기능을 확장하거나 수정할 수 있어야 함.
* 인터페이스 최소주의 원칙: 인터페이스를 통해 메서드를 외부에 제공할 때는 최소한의 메서드만 제공하라는 것.(그 역할에 충실한 최소한의 기능만 공개하라는 것)

### 의존 역전 원칙 (DIP, Dpendency Inversion Principle)
> 고수준 모듈은 저수준 모듈의 구현에 의존해서는 안되며, 저수준 모듈이 고수준 모듈에 의존해야 한다는 것.
> 추상화된 것은 구체적인 것에 의존하면 안된다. 구체적인 것이 추상화된 것에 의존해야한다.
> 자주변경되는 구체 클래스에 의존하지 마라.
> 비지니스와 관련된 부분이 세부 사항에는 의존하지 않는 설계원칙
  * 고수준 모듈: 입력과 출력으로부터 먼(비지니스와 관련된) 추상화된 모듈
  * 저수준 모듈: 입력과 출력으로부터 가까운(HTTP, 데이터베이스, 캐시 등과 관련된) 모듈
* 자신보다 변하기 쉬운 것에 의존하던 것을 추상화된 인터페이스나 상위 클래스를 두어 변하기 쉬운 것의 변화에 영향받지 않게 하는 것.
* 상위클래스일수록, 인터페이스일수록, 추상클래스일수록 변하지 않을 가능성이 높기에 하위 클래스나 구체 클래스가 아닌 상위클래스,      
  인터페이스, 추상클래스를 통해 의존하라는 것이 의존 역전원칙
* 예시 **JDBC**

### 관심사의 분리 (SoC Separation Of Concerns)
> 관심이 같은 것끼리는 하나의 객체 안으로 또는 친한 객체로 모으고, 관심이 다른 것은 가능한 따로 떨어져 서로 영향을 주지 않도록 분리해야한다.
* 하나의 속성, 하나의 메서드, 하나의 클래스, 하나의 모듈,또는 하나의 패키지에는 하나의 관심사만 들어있어야 한다는 것
* 관심사가 다르고 변화의 시기가 다르면 분리해야한다
  