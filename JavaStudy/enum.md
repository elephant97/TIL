# enum	:pushpin:

> 고정 된 값은 '상수' 라고 부른다.

### enum은 무엇인가?
* 클래스가 상수만으로 만들어져 있을 때 enum class를 만들어 사용하는 것

### enum 클래스의 구성
* enum 클래스에 있는 상수들은 지금까지 살펴본 변수들과 다르게 별도로 타입을 지정할 필요도, 값을 지정할 필요도 없다.
* 상수들의 이름만 콤마로 구분하여 나열해 주면 된다.
```java
//상수값을 지정하지 않는 경우
public enum OberTimeValues {
  MONDAY,
  TUSEDAY,
  WENDSDAY;
}

//상수값을 지정하지 않는 경우
public enum OberTimeValues2 {
  MONDAY(1000),
  TUSEDAY(1001),
  WENDSDAY(1002);
  private final int amount;
  OberTimeValues2(int amount){ // 생성자의 경우 package-private와 private만 접근제어자로 사용가능.
    this.amount = amount;
  }
}
```

### enum 클래스의 특징
* "enum 클래스이름.상수이름"을 지정함으로써 클래스의 객체 생서잉 완료 됨
* ⭐enum 클래스는 생성자를 만들 수 있지만, 생성자를 통해 객체를 생성 할 수는 없다.
* enum에 상수값을 지정하는 것은 가능하지만, 동적으로 값을 할당할 수는 없다.
* ⭐enum 클래스의 생성자는 아무것도 명시하지 않는 package-private와 private만 접근제어자로 사용할 수 있다.
* 각 상수를 enum클래스 내에서 선언할 때에만 이 생성자를 사용할 수 있다.
* 생성자가 없는 경우 컴파일 시 자동으로 생성자를 만들어 줌

### enum클래스 생성자 호출
* 아래와 같이 하면 amount값으로 1000이 들어가게 됨
```java
OberTimeValues2 value = OberTimeValues.MONDAY;
```

### Enum의 클래스의 부모 클래스는 반드시 'java.lang.Enum'
* enum 클래스는 무조건 java.lang.Enum이라는 클래스의 상속을 받는다.
* enum 클래스 컴파일 시, 자동으로 컴파일러가 extends java.lang.Enum을 추가해 빌드함.
* 다중상속이 불가능 하기 때문에 enum클래스는 내가 따로 다른 상속을 지정할 수 없음.
* 다른 enum을 상속 선언할 수 없음.
  
### Enum 클래스의 생성자 
  ```java
  protected Enum(String name, int ordinal)
  ```
* 컴파일러에서 자동으로 호출되도록 해놓은 생성자지만, 개발자가 이 생성자를 호출할 수는 없다.   

### Enum클래스의 부모클래스는 Object클래스 이다. 다만 Object클래스 중 4개의 메소드를 Overriding하지 못하도록 막아 놓았다!
* 오버라이딩 못하는 4개의 메서드는 무엇?,(Enum class에서 final로 오버라이딩 되어 선언되어있기 때문에)
  * clone()
    > 객체를 복제하기 위한 메소드, Enum class에서 사용 시 CloneNotSupportedException 이라는 예외 발생됨.
  * finalize()
    > GC가 발생할 때 처리하기 위한 메소드
  * hashcode()
    > int타입의 해시코드 값을 리턴하는 메소드
  * equals()
    > 두 객체가 동일한지 확인하는 메소드
* clone(), fialize()는 사용 하지 않아야 함. hashcode()와 equals()는 사용해도 괜찮다 Overriding만 하지 말 것!   

### Enum class에서 Overriding되어있지만 유일하게 final로 선언되어 있지 않은 메서드 'toString()'
* 기본적으로 enum변수에 이 메소드를 호출하면 상수 이름을 출력함
* 이 메소드는 유일하게 Overriding해도 상관 없다.   

### Enum 클래스에 선언 되어있는 메소드
* compareTo(E e)
  > 매개 변수로 enum타입과의 순서(ordinal) 차이 리턴
  >
  > 순서가 다른지 같은지 비교하는데 사용 됨.
  >
  > 같은 상수라면 0을 그렇지 않고 다르면 순서의 차이를 출력 (매개변수로 넘기는 상수 기준으로 앞에있으면 음수(-) 뒤에있으면 양수(+)를 리턴함)
* getDeclaringClass()
  > 클래스 타입의 enum을 return함
* name()
  > 상수 이름을 return
* ordinal()
  > 상수의 순서 return
* valueOf(Class<T> enumType, String name)
  > static 메서드임. 첫번째 매개변수로 클래스 타입의 enum을, 두번쨰 매개변수로 상수 이름을 넘겨주면 됨


### enum 클래스에 선언되어 있는 모든 상수를 배열로 리턴하기
* values()는 static으로 선언되어 있기 때문에, 객체를 생성하지 않고도 아래와 같이 호출 가능
```java
  OverTimeValues []valueList =  OverTimeValues2.values();
  for(OverTimeValues value:valueList)
    System.out.println(value);
```
* 위와 같이 호출 시 enum 클래스에 있는 상수 이름들이 출력 됨.
