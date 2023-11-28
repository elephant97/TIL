# enum	:pushpin:

## 고정 된 값은 '상수' 라고 부른다.

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

