# Serializable 📌
> 생성한 객체를 파일로 저장하거나, 저장한 객체를 읽거나, 객체를 다른 서버로 보내거나, 다른 서버에서 생성한 객체를 받을 때 해당 인터페이스를 사용함.     
> 해당 인터페이스를 구현하면 JVM에서 해당 객체는 저장하거나 다른 서버로 전송할 수 있도록 해줌

### SerialVersionUID
> serializable 인터페이스를 구현한 후에는 serialVersionUID라는 값을 지정해 주는 것을 권장 함
* **반드시 Static final long으로 선언해야 함**
* 이 값은 해당 객체의 버전을 명시하는데 사용함
* 각 서버가 해당 객체가 같은지 다른지를 확인할 수 있도록 하기 위해서 serialVersionUID로 관리를 해주어야 한다.
* 클래스 이름이 같더라도 해당 ID가 다르면 다른 클래스라고 인식함
* 같은 UID라고 할지라도, 변수의 개수나 타입 등이 다르면 이 경우에도 다른 클래스로 인식함.
* Serializable 객체의 형태가 변경되면 컴파일 시 serialVersionUID가 다시 생성됨
* 데이터가 바뀔 때 마다 serialVersionUID의 값을 변경하는 습관을 가져야만 데이터에 문제가 발생하지 않음.

### ObjectOutputStream과 ObjectInputStream
* ObjectOutputStream
  > 해당 클래스를 사용하면 객체를 저장할 수 있다.
  * Write()메소드를 사용하여 int값을 저장하고, writeByte()메소드로 바이트 값을 저장할 수 있다.
* ObjectInputStream
  > 해당 클래스를 사용하면 객체를 읽을 수 있다.

### transient예약어
* 객체를 저장하거나 다른 JVM으로 보낼 때, transient라는 예약어를 사용하여 선언한 변수는 Serializable 대상에서 제외된다.
* 보안상 중요한 변수나 꼭 지정해야 할 필요가 없는 변수에 대해서는 해당 예약어를 사용하여 제외할 수 있다.
