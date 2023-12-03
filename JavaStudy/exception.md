# Exception	 :pushpin:

### 예외의 출력
* 예외의 첫줄에는 어떤 예외가 발생했는지 출력
* 그 다음 줄 부터는 앞에 탭을 주고 at으로 시작하는 스택 호출 추적(스택 트레이스) 문장들이 출력 됨.
* 예외가 발생한 클래스와 메소드 이름 줄의 번호를 출력
* 그 아래에는 그 메소드를 호출한 클래스와 메소드의 이름, 줄의 번호가 출력 됨

### Try-catch 블록
* try에는 예외가 발생하는 문장들을 묶어 줌.
* catch 괄호 안에 예외가 발생하는 부분만 묶어 줌.
* try-catch에서 예외가 발생하지 않을 경우
  * try내에 있는 모든 문장이 실행되고, try-catch 문장 이후의 내용이 실행된다.
* try-catch에서 예외가 발생하는 경우
  * try내에서 예외가 발생한 이후의 문장들은 실행되지 않는다.
  * catch 내에 있는 문장은 반드시 실행되고, try-catch 문장 이후의 내용이 실행된다.
> System.out이 아닌 System.err로 기입 시 개발도구 IDE에서 출력결과가 다른 색으로 표시 됨.   
> try블록 내에서 선언한 변수를 catch에서 사용할 수 없음.

### finally
* 해당 블록은 예외 발생 여부와 상관 없이 실행 됨.
  > 어떤 경우에 사용될 지 생각해보니, 파일을 읽을 때 파일을 open한 상태에서 예외가 발생했을 시 무조건 파일을 닫아주어야 하는데,   
  > 그 경우에 finally를 사용하면 될 것 같음!

### Try-catch의 정리
* try 다음에 오는 catch 블록은 1개 이상 올 수 있다.
* 먼저 선언한 catch 블록의 예외 클래스가 다음에 선언한 catch블록의 부모에 속하면, 자식에 속하는 catch 블록이 실행되지 않으니,<br>상속 때 처럼 자식에 속하는 것 순서로 catch문을 구성해야 함.
* 하나의 try블록에서 예외가 발생하면 그 예외와 관련이 있는 catch블록을 찾아서 실행
* catch 블록 중 발생한 예외와 관련이 있는 블록이 없는 경우, 예외가 발생되면서 해당 쓰레드는 끝난다.

<br>

## 예외의 종류

### Error
* 에러란 자바 프로그램 밖에서 발생한 예외를 말함.
* Exception클래스는 에러가 아니다.
* 프로그램 오류 발생 시, 오류의 이름이 Error로 끝나는 경우 오류, Exception으로 끝나는 경우 예외
* Error와 Exception으로 끝나는 오류의 가장 큰 차이는 프로그램 안에서 발생했는지, 밖에서 발생했는지 여부이다
* ⭐ Error는 프로세스에 영향을 주어 프로그램이 멈추어 버리고, Exception은 쓰레드에만 영향을 주므로 프로그램을 계속 실행 시킬 수 있음

### Runtime exception(이하 런타임 예외)
* 예외가 발생할 것을 미리 감지 못했을 때 발생함.
* 런타임 예외에 해당하는 모든 예외들은 RuntimeException을 확장한 예외이다.
* 컴파일할 때 예외가 발생하지 않지만, 실행 시 발생할 가능성이 있음
* 컴파일시에 체크를 하지 않기 때문에 unchecked exception이라고도 부름

### Exception과 Error의 공통 부모 클래스 Throwable 클래스
> object 클래스 역시 공통 부모클래스임
* Exception과 Error 처리 시 Throwalbe로 처리해도 무관함.
* 상속 관계가 이렇게 되어 있는 이유는 Exception이나 Error의 성격은 다르지만, 모두 동일한 이름의 메소드를 사용하여 처리할 수 있게 하기 위함임.

### Throwable의 생성자
* Throwable()
* Throwable(String message)
* Throwable(String message, Throwable cause)
* Throwable(Throwable cause)
> 예외 메세지를 String으로 넘겨줄 수도 있고, 예외의 원인을 Throwable 객체로 넘겨 줄 수도 있음.

### Exception에서 overriding한 메소드 중 3가지
* getMessage()
  * 예외 메세지를 String형태로 제공
* toString()
  * 예외 메세지를 String 형태로 제공 받고, getMessage() 보다는 약간 더 자레하기 예외 클래스 이름도 같이 제공
* printStackTrace()
  * 가장 첫 줄에는 예외 메세지 출력, 두 번째 부터는 예외가 발생하기 된 메소드들의 호출 관계(스택트레이스)를 출력해줌.

### Throws와 Throw
* 메소드 선언 시 매개 변수 소괄호 뒤에 throws라는 예약어를 적어 준 뒤 예외 선언 시 해당 메소드에서 선언한 예외가 발생했을 때 호출한 메소드로 예외가 전달 됨.
* 메소드에서 두 가지 이상의 예외를 던질 수 있다면, implements처럼 콤마로 구분하여 예외 클래스 이름을 적어주면 됨.
* try블록 내에서 예외를 발생시킬 경우 throw라는 예약어를 적어 준 뒤 예외 객체를 생성하거나 생성되어있는 객체를 명시 해 줌.
  ```java
    public void throwsException(int number) throws Exception{
      if(number>12){
        throws new Exception("Number is over than 12");
      }
    }
  ```
* throw한 예외 클래스가 catch 블록에 선언되어 있지 않거나, throws 선언에 포함되어 있지 않으면 컴파일 에러 발생
* catch 블록 에서 예외를 throw할 경우에도 메소드 선언의 throws 구문에 해당 예외가 정의 되어 있어야만 한다.
* ⭐ 예외를 throw하는 이유는 해당 메소드에서 예외를 처리하지 못하는 상황이거나, 미처 처리하지 못한 예외가 있을 경우에 대비하기 위함.

### 임의의 Exception
* Exception을 처리하는 예외 클래스를 개발자가 임의로 추가해서 만들 수 있다.
* 반드시 Throwable이나 그 자식의 클래스를 상속 받아야만 한다.
* Throwable클래스의 상속을 받아도 되지만, Exception을 처리하는 클래스 라면 java.lang.Exception 클래스의 상속을 받는 것이 좋음.
* 자식클래스로 throw시 부모 클래스로 catch해도 괜찮음.
* 예외 클래스를 임의로 만들 때 반드시 Throwable의 직계 자손 클래스들을 상속 받아 만들어야만 함.
* 항상 발생하지 않고, 실행시에 발생할 확률이 매우 높은 경우 런타임 예외로 만드는 것이 나을 수 있음.
* 반드시 try-catch로 묶어주어야 하는 경우에만 Exception클래스 확장.
* 실행 시 예외 처리 할 수 있는 경우에는 RuntimeException클래스를 확장하는 것 권장.

