# java.lang 패키지 📌
> java.lang 패키지에 있는 클래스 들은 import를 안해도 사용할 수 있는 유일한 패키지 이다.
> java.lang과 java.util 패키지 안에는 다양한 일을 하는 클래스와 인터페이스 들이 혼재되어있음.

### java.lang 패키지에서 제공하는 인터페이스, 클래스, 예외 클래스 분류
* 언어 관련 기본
* 문자열 관련
* 기본 자료형 및 숫자 관련
* 쓰레드 관련
* 예외 관련
* 런타임 관련
* 기본 어노테이션
  > Deprecated
  > Override
  > Suppress Warnning

### java에서 발생하는 주요 에러
* OutOfMemoryError(OOME) 
  * 메모리가 부족하여 발생하는 에러
  * 메모리 누수가 있거나, Heap의 공간이 부족할 때 발생할 수 있음
  * 대용량 데이터 처리 시 메모리 소비가 증가하여 발생할 수 있으므로 스트림이나,효율적인 데이터 구조를 사용해야함
* StackOverFlowError 
  * 호출된 메소드의 깊이가 너무 깊을 때 발생
  * Strac이라는 영역에 메소드가 어떤 메소드를 호출했는지에 대한 정보를 관리하는데 재귀호출 메소드 잘못 작성 시
    스택에 쌓을 수 있는 메소드 호출 정보의 한계를 넘어설 수 있는데 그 때 발생하는 에러가 StackOverFlowError임

### 숫자를 처리하는 클래스
> 간단한 계산을 할 때 대부분 기본 자료형을 사용하며, 이 기본 자료형은 Stack에 저장되고 관리 됨.   
> 기본 자료형을 사용하여 계산 시 보다 빠른 처리가 가능함.
> 하지만 기본 자료형의 숫자를 객체로 처리해야할 필요가 있을 수 있어 기본자료형으로 선언되어 있는 타입의 클래스들이 선언 되어있음.
  * 특징
    * Character와 Boolean을 제외한 숫자를 처리하는 클래스는 **감싼(Wrapper)클래스** 라고 부르며, **Number abstract 클래스 확장 함**
    * 겉으로는 참조자료형이지만, 기본 자료형처럼 사용 가능하며, 컴파일러에서 자동으로 형 변환을 해줌
    * Character클래스를 제외한 모든 클래스에 Parse타입이름(), valueOf() 메소드를 제공하며, 두 메서드 모두 String과 같은 문자열을 숫자 타입으로 변환 함.
        * Parse타입이름()
          * 기본 자료형 return
        * valueOf()
          * 참조 자료형 return
    * Character와 Boolean을 제외한 클래스 들은 필요 시 기본 자료형 처럼 사용할 수 있으며, new를 사용하여 객체를 만들 지 않아도 값을 할당할 수 있다.
    * 돈 계산과 같이 중요한 연산을 수행할 때, 정수형은 BigInteger 소수형은 BinDecimal을 사용하여야 정확한 계산이 가능하며,
      이 두 클래스 모두 java.lang.Number 클래스의 상속을 받았으며, java.math 패키지에 선언 되어있음
  * 이러한 클래스의 존재 이유
    * 매개 변수를 참조 자료형으로 만 받는 메소드를 처리하기 위해
    * 제네릭과 같이 기본 자료형을 사용하지 않는 기능을 사용하기 위해
    * MIN_VALUE(최소값)나, MAX_VALUE(최대값)와 같이 클래스에 선언된 상수 값을 사용하기 위해
    * 문자열을 숫자로, 숫자를 문자열로 쉽게 변환하고, 2,8,10,16 진수 변환을 쉽게 처리하기 위해 ex) 16진수 toHexString, 2진수 toBinaryString
      
### 각종 정보를 확인하기 위한 System 클래스
> 이 클래스의 가장 큰 특징은 생성자가 없다는 것이다.   
> System 클래스의 3개의 static 변수가 선언되어있다.
> PrintStream과 InputStream은 모두 java.io패키지에 선언되어 있음    
> 즉, 실제 System 클래스에 선언되어 있는 메소드들은 출력과 관련된 것은 없으며, System 이름 그대로 시스템에 대한 정보를 확인하는 클래스 이다.   
> *출력과 관련된 메서드는 PrintStream클래스에서 찾아야 함*  
  * static으로 선언되어 있는 타입과 변수 명
    * static PrintStream **err** : 에러 및 오류를 출력할 때 사용
    * static InputStream **in** : 입력값을 처리할 때 사용
    * static PrintStream **out** : 출력값을 처리할 때 사용
      > println()이라는 메서드가 PringtStream 클래스에 선언되어있으며, static 메서드 이다.
  * System에서 제공되는 메소드 분류
    *아래의 메소드 중 GC수행과 JVM 종료 관련 메소드는 절대로 수행해서는 안됨*
    * 시스템 속성(Property)값 관리
      * Properties는 java.util 패키지에 속하며, Hashtable의상속을 받은 클래스 이다.
      * 자바 프로그램 실행 시 Preperties 색체가 생성되며, 어디서 든지 같은 JVM 내에서는 꺼내서 사용 가능함
    * 시스템 환경(Enviorment)값 조회
      * getenv() 는 Map<String,String> 타입으로 return
    * GC 수행
      * 아래 메소드 들을 실행시켰을 시 시스템은 하려던 일을 멈추고 이 작업을 실행함.
      * gc() : 가비지 컬렉터 실행
      * runFinalization() : GC 처리를 기다리는 모든 객체에 대하여 finalize()메소드 실행
    * JVM 종료
      * exit() : 현재 수행중인 JVM을 멈춤 정상종료 시 0 return 그 외의 숫자는 비정상 종료 의미
    * 현재시간 조회
      * currentTimeMillis() : 현재 시간을 밀리 초 단위로 리턴함. 현재 시간을 나타낼 때 사용
      * nanoTime() : 현재 시간을 나노초 단위로 리턴함. 시간의 차이를 측정하기 위한 용도의 메소드
    * 기타 관리용 메소드들

### Sytem.out
> out과 err변수는 PrintStream이라는 동일한 클래스의 객체이며, 단지 정상적인 출력인지 에러가 났을 때 출력 결과인지 차이만 존재함.
> PrintStrem 클래스는 static하게 사용 함.
  * PrintStrem 클래스의 출력을 위한 주요 메소드
    > print와 println에서 받는 매개변수가 **byte와 short 타입**인 경우 둘다 정수형이기 때문에 int 타입으로 알아서 처리해서 출력 함
    > **print와 println메소드 에서는 단순히 toString()메소드 결과를 출력하는 것이 아닌, String의 valueOf()라는 static 메소드를 호출하여 결과를 받아 출력 함**   
    > 객체를 출력할 때에는 toString()보다 valueOf()메소드를 사용하는 것이 훨씬 안전함
    * println()
      * **매개변수가 없는 메소드가 존재 함**
    * print()
    * format()
    * printf()
    * write()

### toString과 valueOf의 차이
  * toString은 객체의 "문자열 표현"
  * valueOf는 매개변수로 받은 값을 해당 타입의 문자열 표현으로 반환
  * valueOf()는 다양한 기본 데이터 타입을 문자열로 변환하기 위해 사용되는 반면, toString()은 객체의 자체 표현에 중점을 둔다.
   
