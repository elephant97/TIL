# String  :pushpin:

### String 클래스의 선언부
```java
  public final class String extends Object implements Serializable, Comparable<String>.CharSequence
```
* Serializable   
  * 구현해야 하는 메소드가 하나도 없는 메소드
  * 이 인터페이스 implements 해 놓으면 해당 객체 파일 저장 및 다른 서버 전달 가능
* Comparable
  * comparaTo()라는 메소드 하나만 선언되어 있으며, 객체가 같은지 비교함
  * equals()랑 다른 점은 return이며, 객체의 순서를 처리할 때 유용하게 사용 됨.
* CharSequence
  * 해당 클래스가 문자열을 다루기 위한 클래스라는 것을 명시적으로 나타내는데 사용 됨.

### String의 생성자
```java
  // 기본적으로 다음과 같이 생성함.
  String name = "Sumin, Park";
```
* 다양한 생성자가 있으나, 가장 많이 사용하는 생성자는 다음과 같다.
* String(byte[] bytes)
  > 현재 사용중인 플랫폼의 캐릭터 셋을 이용하여 제공된 byte배열을 디코딩한 String객체를 생성함.
* String(byte[] bytes, String charsetName)
  > 지정한 이름을 갖는 캐릭터 셋을 사용하여 지정한 byte배열을 디코딩한 String 객체를 생성한다.

### String 문자열을 byte로 변환
* getBytes()
  > 기본 캐릭터 셋의 바이트 배열 생성.
* getBytes(Charset charset)
  > 지정한 캐릭터 셋 객체 타입으로 바이트 배열을 생성.
* getBytes(String charsetName)
  > 지정한 이름의 캐릭터 셋을 갖는 바이트 배열을 생성.
*캐릭터셋 변경 시 String으로 바로 변환 x 바이트 변환 -> 바이트 배열을 지정된 캐릭터 셋으로 변경*
  > byte 배열과 String타입의 캐릭터 셋을 받는 생성자
  > getBytes() 메소드 중에서 String타입의 캐릭터 셋을 받는 메소드는
  > **UnsupportedEncodingException을 발생시킬 수 있으므로 try-catch로 감싸주어야함**

### 모든 객체를 처리할 때에는 널 체크를 반드시 해야만 한다.
* == 비교와 != 비교로 널 체크 가능

### String의 내용을 비교하고 검색하는 메소드 
* 문자열의 길이를 확인하는 메소드
  * length()
    > 문자열의 길이를 리턴한다.

<br>

* 문자열이 비었는지 확인하는 메소드
  * isEmpty()
    > 문자열이 비어있는지를 확인함. 비어있으면 true 리턴
<br>

* 문자열이 같은지 비교하는 메소드
  * equals(Object anObject)
  * equalsIgnnoreCase(String anotherStr)
  * compareTo(String anotherStr)
    > 보통 정렬할 때 사용함
    > 알파벳 순으로 앞에 있으면 양수, 뒤에 있으면 음수 리턴
  * compareToIgnoreCase(String str)
  * contentEquals(CharSequence cs)
    > String, StringBuffer, StringBuilder 모두 사용 가능한 같은지 비교 하는 메소드
  * contentEquals(StringBuffer sb)
  *Case가 포함된 메소드들은 대소문자와 관련 된 메소드임*

<br>

* 특정 조건에 맞는 문자열이 있는지를 확인하는 메소드
  * startsWith(String prefix)
  * startsWith(String prefix, int toffset)
    > 매개 변수로 넘어온 값으로 시작하는 지 탐색
  * endsWith(String suffix)
    > 매개변수로 넘어온 값으로 끝나는 지 탐색
  * contains(CharSequence s)
    > 해당 문자열을 포함하는 지
  * matches(String regex)
    > contains과 동일하지만 반드시 정규표현식을 이용해야함
  * regionMatches(boolean ignoreCase, int toffset, String other, int ooffset, int len)
    > 특정 영역이 동일한가. ignoreCase에는 대소문자 가릴지 안가릴지 true false로 지정하면 됨
    > toffset 비교 대상 문자열 확인 시작 위치   
    > ooffset other의 비교 위치   
    > 비교 개수
  * regionMatches(int toffset, String other, int ooffset, int len)


### ⭐Constant Pool
* 객체의 재 사용을 위한 것
```java
  String text="Check value"
  String text2="Check value"
```
* 이렇게 두개 동시에 선언했을 때 text와 text2가 같은 값을 가지고 있으므로 == 비교시 true가 도출 됨
* Constane pool에 이미 만든 객체를 재 사용 했기 때문
* **String의 경우 동일한 값을 갖는 객체가 있으면 이미 만든 객체를 재사용한다**
  <br>
```java
  String text="Check value"
  String text2=new String("Check value");
```
* 이렇게 String객체를 생성하면 값이 같은 String 객체를 생성한다고 하더라도 Constant pool의 값을 재활용 하지 않고 별도의 객체 생성
* 따라서 이런 경우 == 비교시 false가 도출 됨
* 이때 **intern()**을 사용한다면 풀에 값을 할당하게 되어, 객체를 생성한 경우에도 ==로 비교가 가능하지만
  **억지로 문자열 풀에 값을 할당하도록 만들면 저장 영역의 한계로 인해 메모리 청소가 일어나 전체 자바의 악영향을 끼치기 때문에 절대 사용하지 말 것**

### String에서 위치를 찾아내는 방법
> 각 메서드의 매개변수 개수는 여러가지가 있음 
* indexof(int ch)
  > 앞에서 부터 문자열이나 char 찾음
* lastIndexOf()
  > 뒤에서 부터 찾음

### String의 값의 일부를 추출하기 위한 메소드
* char 단위의 값을 추출하는 메소드
  * charAt(int index)
    > 해당 위치의 char을 추출
  * getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)
    > 매개변수로 넘어온 dst의 srcBegind에서 srcEnd를 저장한다 dst의 시작 위치는 dstBegin이다.
  * codePointAt(int index)
    > 특정 위치의 유니코드 값 리턴. 리턴 타입이 int이지만 이 값을 char로 형 변환하면 char 값 출력 가능
  * codePointBefore(int index)
    > 특정 위치 **앞**의 유니코드 값 리턴. 리턴 타입이 int이지만 이 값을 char로 형 변환하면 char 값 출력 가능
  * codePointCount(int beginIndex, int endIndex)
    > 지정한 범위에 있는 유니코드 개수를 리턴
  * offsetByCodePoints(int index, int codePointoffset)
    > 지정된 index부터 오프셋이 설정된 인덱스를 리턴   
    > 문자열 인코딩과 관련된 문제를 해결하기 위해 사용.
    > 한글의 경우 한 글자로 인식됨

<br>

* char 배열의 값을 String으로 변환하는 메소드
  * copyValueof(char[] data)
    > char 배열에 있는 값을 문자열로 변환
  * copyValueOf(char[] data, int offset, int count)
    > char 배열에 있는 값을 문자열로 변환하는데 offset부터 count개수만큼 만 문자열로 변환함
  ```java
    //static 메소드 이기 때문에 현재 사용하는 문자열을 참조하여 생성하는 것이 아닌, Static하게 호출하여 사용해야함
    String text = String.copyValueOf(values);
  ```

<br>

* String의 값을 char배열로 변환하는 메소드
  * toCharArray()
    > 문자열을 char배열로 변환하는 메소드
    > 성능과 메모리 활용성을 고려하여 Java 9부턴 byte배열로 내부적으로 저장함

<br>

* 문자열의 일부 값을 잘라내는 메소드
  * substring(int beginIndex)
    > beginIndex부터 끝까지 대상 문자열을 잘라 String으로 리턴
  * substrring(int beginIndex, int endIndex)
    > beginIndex부터 endIndex까지 대상 문자열을 잘라 String으로 리턴
  * subSequence(int beginIndex, int endIndex)
    > beginIndex부터 endIndex까지 대상 문자열을 잘라 CharSequence타입으로 리턴

<br>

* 문자열을 여러개의 string배열로 나누는 split 메소드
  * split(String regex)
    > reqex에 있는 정규 표현식에 맞추어 문자열을 잘라 String배열로 리턴
  * split(String regex, int limit)
    > reqex에 있는 정규 표현식에 맞추어 문자열을 잘라 String배열로 리턴, 이때 String배열의 크기가 limit 보다 크면 안됨

### String값을 바꾸는 메소드

* 문자열을 합치는 메소드와 공백을 없애는 메소드
  * concat(String str)
    > str을 기존 문자열 우측에 붙인 새로운 문자열 객체를 생성하여 리턴
  * trim()
    > 문자열의 맨 앞과 맨 뒤에 있는 공백들을 제거한 문자열 객체를 리턴함.

<br>

* 내용을 교체(replace) 하는 메소드
  * replace(...)
    > 해당 문자열에 있는 oldChar값을 newChar값으로 대치
  * replaceAll(String regex, String replacement)
    > 해당 문자열의 내용 중 regex 정규 표현식에 포함되는 모든 내용 대치
  * replaceFirst(String regex, String replacement)
    > regex에 표현된 정규 표현식에 포함되는 첫번째 내용을 replacement로 대치

<br>

* 특정 형식에 맞춰 값을 치환하는 메소드
  * **static String** format(String format, Object... args)
    > format에 있는 문자열의 내용 중 변환해야 하는 부분의 내용을 args로 변환
  * **static String** format(Locale l,String format, Object... args)
    > Locale타입의 l에 선언된 지역에 맞추어 출력
    ```java
      // 아래와 같이 작성 시 한국의 원화 규칙에 맞춰 000단위마다 ,가 찍힘
      String.format(Locale.KOREA,"₩ %,d",money)
    ```

<br>

* 대소문자를 바꾸는 메소드
  * toLowerCase()
    > 소문자 변경
  * toLowerCase(Locale locale)
    > 지역 정보에 맞추어 모든 문자열의 내용을 소문자로 변경
  * toUpperCase()
    > 대문자 변경
  * toUpperCase(Locale locale)
    > 지역 정보에 맞추어 모든 문자열의 내용을 대문자로 변경

<br>

* 기본 자료형을 문자열로 변환하는 메소드
  * **static String** valueOf(모든 자료형)   
  *모든 자료형은 null일 경우 toString메소드 사용 불가능 (NullPointerExeception발생) 그럴 때 vlaueOf 사용 시 "null"이라는 문자열 출력해줌*

### immutable(불변의)한 String의 단점을 보완하는 StringBuffer와 StringBuilder
```java
  String text="Hello";
  text = text+" World";
```
> String객체는 변하지 않는다.   
> 즉, 위의 경우에 Hello만 들어있던 객체는 더이상 사용할 수 없고, 버려진다 계속 문자열을 더하면 쓰레기를 계속 만든 다는 것   
> 이 단점을 보완하기 위해 StringBuffer와 StringBuilder 탄생

* StringBuilder
  * Thread safe하지 않음
  * StringBuffer보다 빠르지만 여러 스레드가 동시에 접근할 수 있는 경우 충돌이 생길 수 있음
* StringBuffer
  * Thread safe함
* append()로 문자열 이어붙이기 가능
  > JDK 5 이상에서 String에 + 연산을 할 시 자동으로 StringBuffer로 변환해 줌 하지만, for문 같이 반복연산에는 자동 변환하지 않으니 필요함.
  
** String, StringBuilder, StringBuffer세가지 중 하나의 클래스를 매개변수로 받는 작업 시 CharSequence타입으로 받는 것이 좋음**
 
