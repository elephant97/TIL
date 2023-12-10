# IO 📌
> 파일에 읽거나 저장할 일이 있을 때
> 다른 서버나 디바이스로 보낼 일이 있을 때      
> JVM 기준으로 읽을 때에는 Input을 파일로 쓰거나 외부로 전송할 때에는 Output이라는 용어 사용

### java.io 패키지
> 이 패키지에서는 바이트 기반의 데이터를 처리하기 위해서 여러 종류의 스트림이라는 클래스를 제공함.
* 바이트 기반의 데이터를 처리하기 위해서 읽는 작업은 InputStream을, 쓰는 작업은 OutputStream을 통해 작업하도록 되어있다.
* 바이트가 아닌 char 기반의 문자열로만 되어있는 파일은 Reader와 Writer라는 클래스로 처리함
* **스트림이라는 것은 끊기지 않고 연속적인 데이터를 말함**

### 자바의 File과 Files 클래스
> 이 클래스의 이름은 File이지만 파일의 경로 정보도 포함함
> 파일 및 경로 정보를 통해 통제하기 위한 클래스 
* File클래스는 정체가 불분명하고, 심볼릭 링크와 같은 유닉스 계열의 파일에서 사용하는 몇몇 기능을 제대로 제공하지 못하여 NIO2가 등장하면서 Files로 대체하여 사용
* File클래스는 객체를 생성하여 데이터를 처리하는 반면, Files클래스는 모든 메소드가 **static으로 선언되어 있기 때문에** 별도의 객체를 생성할 필요 없다.
* file 객체가 가리키는 것이 파일이 아닌 경로일 경우에는 해당 경로에 있는 파일의 목록을 가져오거나, 경로를 생성 및 삭제하는 기능을 제공

### File 객체 생성자
> OS마다 디렉터리를 구분하는 기호가 다르므로 File 클래스에 separator라는 것이 static변수로 존재하니 사용하면 됨
* File(File parent, String child)
  > 이미 생성되어 있는 file 객체(parent)와 그 경로이 하위 경로 이름으로 새로운 File 객체를 생성함
* File(String pathname)
  > 지정한 경로 이름으로 File객체를 생성한다
* File(String parent, String child)
  > 상위 경로와 하위 경로로 File객체를 생성      
  > 전체 경로와 파일 이름으로 지정 되어있을 경우 파일을 가리키는 File객체가 된다.
* File(URI uri)
  > URI에 따른 File 객체를 생성

### mkdir() mkdirs() 메소드
> 존재하지 않는 디렉터리를 File 클래스를 사용하여 만들라면 이와 같은 메소드를 사용하면 된다
* mkdir()
  > 디렉터리를 하나만 만듬
* mkdirs()
  > 여러개의 하위디렉터리를 만듬

### createNewFile() 
> 해당 메소드는 IOException을 던진다고 정해져 있기 때문에 try-catch로 묶어주어야 하며, 정상적으로 컴파일 하기 위해서
> java.io.IOException 클래스를 import 해주어야 함.

### InputStream과 OutputStream
> InputStream과 OutputStream은 abstract클래스를 통해 제공 됨
> 매번 쓰기 작업을 요청할 때마다 저장하면 비요율적이기 때문에 한번에 버퍼에 담았다가 **flush()** 를 통해 저장 함
* 어떤 리소스를 열었던 간에 이 인터페이스를 구현하면 해당 리소스는 **close()** 메소드를 이용하여 닫아주어야 함
* **FileInputStrema, ObjectInputStream**은 객체를 생성해서 데이터 처리
* **FilterInputStream** 의 클래스는 protected로 선언되어 있기 때문에 상속받은 클래스에서만 객체 생성
* FileInputStream은 텍스트파일을 읽기 위한 용도라기 보다 이미지와 같이 바이트 코드로 된 데이터를 읽을 때 사용 됨
  
### Reader와 Writer
> Stream은 byte를 다루기 위한 것이며, Reader와 Writer는 char기반의 문자열을 처리하기 위한 클래스이다.
* Reader
```java
//선언부
public abstract class Reader extends Object implements Readable, Closeable
```
  * abstract로 선언되어 있다.
  * Reader를 확장한 주요 클래스
    * BufferRedaerm CharArrayReader, FilterReader, InputStreamReader, PipedReader, StringReader
* Writer
```java
//선언부
public abstract class Writer extends Object implements Appendable, Closeable, Flushable
```
  * Appendable 인터페이스는 Java 5에서 추가되었으며 각종 문자ㅕㅇㄹ을 추가하기 위해 선언
  * String 객체를 추가하려면 write()를 사용하면 되고, Stringbuffer나 StringBuilder를 사용한 경우 append를 사용하여 추가하면 된다.

### FileWriter
> 객체를 생성하고 char 기반의 내용을 파일로 쓰기 위해 사용함
* 해당 객체를 생성할 때 IOException이 발생할 수 있다.
  * 매개 변수로 넘어온 파일 이름이 파일이 아닌 경로를 의미할 경우
  * 해당 파일이 존재하지는 않지만 권한 등의 문제로 생성할 수 없는 경우
  * 파일이 존재하지만 여러가지 이유로 파일을 열 수 가 없는 경우

### BuilderWriter
> Writer에 있는 Write나 append메소드를 사용하여 데이터를 쓰면 메소드를 호출할 때 마다 파일에 쓰기 때문에 매우 비효율 적이다
> 이러한 단점을 보완하기 위하여 BufferWriter라는 클래스가 있다.
* 버퍼라는 공간에 저장할 데이터를 보관해 두었다가 버퍼가 차게되면 데이터를 저장하도록 도와줌

**FileWriter나 BufferWriter변수를 try문 안에서 선언했다면, finally에서 close()메소드를 호출할 수 없으므로 try-catch문 밖에 선언해야함**    
**가장 마지막에 OPEN한 순으로 닫아야만 한다.**

### Scanner 클래스
> 택스트 기반의 기본 자룧ㅇ이나 문자열 데이터를 처리하기 위한 클래스
> 정규표현식을 사용하여 데이터를 잘라 처리할 수 있다.
