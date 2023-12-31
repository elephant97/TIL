# 인터페이스(interface) :pushpin:


### 인터페이스란?
* 몸통이 없는(body) 즉 메소드의 구현부가 없는 메소드가 선언 되어있는 것.
* 인터페이스는 메소드를 사용하는 사용자 입장에서는 내부 구현이 중요하지 안다.
  > 시스템 개발 시 설계 단계에서 인터페이스 라는 것을 만들어 두면 개발할 때 메소드의 이름을 어떻게 할 지,
  > 매개변수를 어떻게 할지를 일일이 고민하지 않아도 됨.
  
  > 설계 단계에서 인터페이스만 만들어 놓고, 개발 단계에서 실제 작업을 수행하는 메소드를 만들면 설계 단계의 산출물과 개발 단계의 산출물이 보다 효율적으로 관리됨.
  
  

### 인터페이스의 가장 일반적인 패턴인 DAO(Data Access Object)패턴
* 이 패턴은 데이터를 저장하는 저장소에서 원하는 값을 요청하고 응답받음

### ⭐인터페이스와 abstract클래스를 사용하는 이유
* 설계 시 선언 해 두면 개발할 때 기능을 구현하는 데에만 집중할 수 있음.
* 개발자에 따라 메소드의 이름과 매개변수 선언의 격차를 줄일 수 있음.
* 공통적인 인터페이스와 abstract클래스를 선언해 놓으면, '선언'과 '구현'을 구분할 수 있음.
* ⭐외부에 노출되는 것을 정의 해 놓고자 할 떄 사용됨.

### 인터페이스의 특징
* 인터페이스의 선언부는 public class로 시작하지 않고, public interface로 시작함.
* interface 내부에 선언된 메소드들은 몸통(body)가 있으면 안 된다.
  > 메소드 선언 이후에 중괄호를 열고 닫거나, 중괄호 안에 한 줄의 코드도 있으면 안 된다.
  
  > 중괄호는 인터페이스 선언을 위한 가장 상위의 중괄호만 있어야 한다.
* 인터페이스 소스파일 이름은 보통 아무런 명시적인 단어를 지정하지 않거나, 클래스 이름 앞에 I를 붙여서 IMemberManager라고 표준한다.
* 내부에 static이나 final 메소드가 선언되어 있으면 안된다.

### 만들어져 있는 인터페이스를 적용할 때(구현할 떄)
* 클래스 선언문에서 클래스 이름 뒤에 implements라는 예약어를 쓴 후 인터페이스들을 나열하면 됨.
* implements 뒤에는 여러개의 인터페이스가 올 수 있음
  ```java
  public class MemberManagerImpl implements MemberManager
  ```
* 인터페이스를 implements하면 "상속한다"고 하지 않고 "구현한다"고 한다.
* 즉 해당 클래스에서 구현해야 하는 인터페이스를 정의함으로써 클래스에 짐을 지어 주는 것.
* 상속은 다중상속이 되지 않지만, 인터페이스는 여러개를 implements할 수 있다.
* ⭐인터페이스를 구현할 경우 (implements 뒤에 인터페이스 이름을 나열 할 경우)는 반드시 인터페이스에 정의된 메소드들의 몸통을(구현부)만들어 주어야 한다.

### 인터페이스의 객체 선언 방법
* 인터페이스 객체변수명 = new 구현부();
* 쉽게 생각하자면 상속관계에 있는 클래스 형 변환 시 부모클래스 = new 자식클래스; 형태를 생각하면 된다.
  > 예시 구현 class) public class MemberManagerImpl implements MemberManager
  ```java
    MemberManger memberManger = new MemberManagerImpl();
  ```
