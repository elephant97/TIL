# 클래스 안의 클래스(NestedClass) 📌
> 클래스 안에 클래스가 들어갈 수 있다.
> 코드를 간단하게 표현하기 위해 존재하며, 자바기반 UI처리를 할 때 사용자의 입력이나, 외부 이벤트에 대한 처리를 하는 곳에서 많이 사용 됨

### Nested 클래스 구분
* 선언한 방법에 따라 *Static nested 클래스, 내부(inner)클래스*로 구분 됨
* 둘의 차이는 *Static으로 선언*되었는지 여부임.
* *내부클래스*의 경우 이름이 있는 "로컬 내부 클래스"와 이름이 없는 "익명 내부 클래스"로 나뉨
* 둘의 차이는 이름이 있는지 없는지에 따라 나뉨

### Nested 클래스 사용 이유
* 한 곳에서만 사용되는 클래스를 논리적으로 묶어 처리할 필요가 있을 때 *static Nested클래스 사용 이유*
* 캡슐화가 필요할 때 즉 내부 구현을 감추고 싶을 때 *inner클래스 사용 이유*
* 소스의 가독성과 유지보수성을 높이고 싶을 때

### Static nested 클래스의 특징
```java
Public class OuterOfStatic {
  static class StaticNested { //Static nested 클래스
  }
}
```
* 빌드 시 nested클래스는 OuterOfStatic$StaticNested.class 파일로 나옴
```java
//호출 시
OuterOfStatic.StaticNested staticNested = new OuterOfStatic.StaticNested();
```
* 겉으로는 유사하지만 내부적으로는 구현이 달라야 할 때 static nested 클래스 사용

### 내부 클래스와 익명 클래스
```java
OuterOfInner outer = new OuterOfInner();
OuterOfInner.Inner inner = outer.new Inner();
```
* 내부 클래스의 경우 캡슐화 때문에 만듬
* 하나의 클래스에서 어떤 공통적인 작업을 수행하는 클래스가 필요한데 다른 클래스에서는 그 클래스가 필요 없는 경우 이렇게 내부클래스를 만들어 이용함
* 내부클래스는 GUI관련 프로그램을 개발할 때 가장 많이 사용
* GUI에서 내부 클래스가 가장 많이 사용되는 부분은 리스너를 처리할 떄임.

### Nested 클래스 참조가능한 변수
* Static Nested 클래스
  * 감싸고 있는 클래스의 static변수만 참조 가능
* 내부클래스와 익명클래스
  * 감싸고있는 어떤 변수라도 참조 가능.
  * 반대로의 참조도 가능함
  * private변수도 참조 가능
