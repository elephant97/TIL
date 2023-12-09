# 제네릭(Generic) 📌
> 실행시에 개발자가 미처 생각하지 못한 부분에서 프로그램에서 예외가 발생할 때가 많다.
> 그러한 경우를 대비하기 위해 메소드 개발과 함께 JUnit과 같은 테스트코드를 작성하는 것이 좋다.   

### JUnit이란?
> 메소드나 클래스 같은 작은 단위를 쉽게 테스트할 수 있도록 도와주는 프레임워크이다.
> 메소드를 테스트하는 코드를 만들어야하고, 테스트 하는 조건에 맞지 않는 경우 실패로 간주하도록 되어있음.
> JUnit을 통해 테스트 코드 작성 시 테스트 수행 결과를 하나하나 눈으로 확인할 필요가 없다.

### 제네릭(Generic)은 무엇인가?
> Java 5에서 새롭게 추가되었으며, 타입 형 변환에서 발생할 수 있는 문제를 사전에 없애기 위해서 만들어짐.
> 사전이라 함은 실행시에 예외가 발생하는 것을 처리하는 것이 아닌, 컴파일 때 점검할 수 있도록 한 것을 말한다.
```java
  //제네릭을 활용한 클래스 선언 예시
  public class CastingGenericDTO<T> implements Serializable{
    private T object;
    public void setObject(T obj){
      this.object = obj;
    }
    public T getObject(){
      return object;
    }
  }
```
 * 꺽쇠 안에 있는 그 이름은 가상의 타입 이름이다.
 * 꺽쇠 안에는 현재 존재하는 클래스를 사용해도 되고, 존재하지 않는 것을 사용해도 되지만 되도록이면   
   클래스의 이름 명명 규칙과 동일하게 지정하는 것이 좋다.
```java
  //제네릭으로 선언한 객체 생성 시 다음과 같이 형 변환이 필요 없게 됨.
  CastingGenericDTO<String> dto1 = new CastingGenericDTO<String>();
  dto1.setObject(new String());
  String temp = dto1.getObject();
  CastingGenericDTO<StringBuffer> dto2 = new CastingGenericDTO<StringBuffer>();
  dto2.setObject(new StringBuffer());
  StringBuffer temp = dto2.getObject();
```
  * 잘못된 타입으로 치환하면 컴파일 자체가 안되므로, 실행 시 다른 타입으로 잘못 형 변환하여 예외가 발생하는 일은 없음.
  * 명시적으로 타입을 지정할 때 사용하는 것이 제네릭.

### 제네릭 타입의 이름 정하기
> 클래스 선언 시 꺽쇠안에 어떤 단어가 들어가더라도 상관은 없으나, 자바에서 정의한 기본 규칙이 있다.
  * E: 요소 (Element, 자바 컬렉션(Collection)에서 주로 사용 됨)
  * K: 키
  * N: 숫자
  * T: 타입
  * V: 값
  * S,U,V: 두 번째, 세 번째, 네 번째에 선언 된 타입

### 제네릭의 Wildcard타입 <?>
> 객체의 타입 대신 ? 사용 시 어떤 타입이 제네릭 타입이 되더라도 상관없지만, 메소드 내부에서는 해당 타입을 정확히 모르기 떄문에
> **Object**로 처리해야만 한다. 이때 ?로 명시한 타입을 Wildcard 타입이라고 한다.
```java
public void wildcardStringMethod(WildcardGeneric<?> c){
  Object value=c.getWildcard();
  if(vlaue instanceof String){// 만약 넘어오는 타입이 두세가지로 정해져 있따면, 다음과 같이 메소드 내에서 instanceof를 사용하여 해당 타입 확인
    System.out.println(value);
  }
```
  * Wildcard는 **메소드의 매개 변수로만 사용하는 것이 좋다.**
  * 어떤 객체를 wildcard로 선언하고, 그 객체의 값은 가져올 수는 있지만 **wildcard로 객체를 선언했을 때에는 특정 타입으로 값을 지정하는 것은 불가능**

### 제네릭 선언에 사용하는 타입의 범위도 지정 가능하다(Bounded Wildcards).
> 제네릭을 사용할 때 <>안에는 어떤 타입이라도 상관 없으나, wildcard로 사용하려는 타입을 제한할 수 있다.
> ?대신 **? extends 타입**으로 작성하면 된다.
> 제네릭 타입의 경계를 지정하는데 사용한다는 의미로 해석.
```java
public void boundedWildcardMethod(WildcardGeneric<? extends Car> c){ //이렇게 선언 시 car를 상속받은 모든 클래스를 사용할 수 있음
  Car value=c.getWildcard();
  System.out.println(value);
}
```
### 메소드를 제네릭하게 선언









