# Java7에서 추가되거나 달라진 것들📌
> - 숫자 표시 방법 보완
> - switch문에서 String사용
> - 예외 처리시 다중 처리 가능
> - 제네릭을 쉽게 사용할 수 있는 Diamond

### 달라진 숫자 표현법
* 0을 숫자 앞에 넣어주면 8진수
* 0x를 숫자 앞에 넣어주면 16진수
* 0b를 숫자 앞에 넣어주면 2진수로 표현 가능하며, 7에서 추가된 내용
* 숫자 사이에 "_"를 넣어 1000단위 구분 가능 ex) 1_000_000

### switch문장의 확대
* Java 7부터는 switch문장에 String 사용 가능
  > string 문자열이 null인 경우 NullPointerException이 발생하므로 null체크 필요

### 제네릭의 diamond
> Java7부터는 이미 변수를 선언할 때 필요한 타입들을 지정해 놓았기 때문에 생성자에 일일히 타입을 명시해 줄 필요가 없다
```java
  HashMap<String, Integer> map = new HashMap<>();
  Map<String,List<String>> map2 = new HashMap<>();
```
* 다이아몬드 사용 시 제약
  * 다이아몬드 미 지정시 컴파일 경고 발생
  * 매소드 내에서 객체 생성시
  * 제네릭하면서도 제네릭하지 않은 객체 생성시

### 다양한 예외처리
* 파이프로 여러 예외 동시처리 가능
```java
  catch(IlleagalArgumentException | FileNotFoundException | NullPointerException exception){
  }
```
* 리소스와 함께 처리하는 Try문장(try-with-resource)
  * Java7에서 AutoCloseable이라는 인터페이스가 추가되었는데, 이 인터페이스를 구현한 클래스는 try-with-resource문에서 별도로
    close()할 필요 없음
  ```java
    try(Scanner scanner = new Scanner(new File(fileName), encoding)){
    }catch(...){
    }
  ```
  * 만약 try의 소괄호 내에서 두개의 객체를 생성할 필요가 있는 경우 세미콜론으로 구분하여 두 객체 생성하면 됨

