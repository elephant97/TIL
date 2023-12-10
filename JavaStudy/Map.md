# Map 📌
> Map은 키와 값이 1:1로 매칭되며, 키는 Map에서 중복되지 않는다.

### Map의 특징
* 모든 데이터는 키와 값이 존재한다.
* 키가 없이 값만 저장될 수는 없다.
* 값 없이 키만 저장할 수도 있다.
* 값 없이 키만 저장할 수도 없다.
* 키는 해당 Map에서 고유해햐 한다.
* 값은 Map에서 중복되어도 전혀 상관 없다.

### Map 인터페이스의 메소드
* **put(K key, V value)**
  > 해당 키와 값을 데이터로 저장한다.
* putAll(Map<? extends K,? extends V> m)
  > 매개변수로 넘어온 Map의 모든 데이터를 저장
* **get(Object key)**
  > 매개변수로 넘어온 키에 해당하는 값을 넘겨줌
* **remove(Object key)**
  > 매개변수로 넘어온 키에 해당하는 값을 넘겨주며, 해당 키와 값은 Map에서 삭제
* keySet()
  > 키의 목록을 **Set타입**으로 리턴
* values()
  > 값의 목록을 **Collection타입**으로 리턴
* entrySet()
  > Map안에 Entry라는 타입의 set을 리턴
* size()
  > Map의 크기를 리턴
* clear()
  > Map의 내용을 지움

### Map을 구현한 주요 클래스
> **HashMap, TreeMap, LinkedHashMap, HashTable**  
> HashTable 클래스는 Map 인터페이스를 구현하기는 했지만 일반적인 Map 인터페이스를 구현한 클래스들과는 다름.

### HashTable과의 차이
* Map은 컬렉션 뷰를 사용하지만, Hashtable은 **Enumeration**객체를 통해서 데이터를 처리함
* Map은 키,값, 키-값 쌍으로 데이터를 순환하여 처리할 수 있지만,Hashtable은 이 중에서 키-값쌍으로 데이터를 순환하여 처리할 수 없음.
* Map은 이터레이션을 처리하는 도중에 데이터를 삭제하는 안전한 방법을 제공하지만, Hashtable은 그러한 기능을 제공하지 않음
  * 키가 값에 null값 저장 가능 여부
    * HashMap (O)
    * Hashtable (X)
  * 쓰레드 안전 여부
    * HashMap (X)
    ```java
    // HashMap을 쓰레드에 안전하게 사용하는 방법
    Map m = Collections.synchronizedMap(new HashMap(...));
    ```
    * Hashtable (O)
  
### 쓰레드에 안전하게 사용하는 방법
* 대부분의 collection 관련 클래스는 **synchronized** 처리를 하거나, 이름에 Councurrent가 포함되어 있어야만 쓰레드에 안전하게 사용 가능.
* ex) ConcurrentHashMap , CopyOnWriteArrayList
* java.util.concurrent 패키지 소속

### HashMap
* HashMap의 상속 관계
  * **java.lang.Object > java.util.AbstractMap<K,V> > java.util.HashMap<K,V>**
* HashMap에서 구현한 인터페이스
  * **Serializable, Cloneable, Map<E>**
  * Serializable : 원격으로 객체를 전송하거나, 파일에 저장할 수 있음을 지정
  * Cloneable : Object 클래스의 colne() 메소드가 제대로 수행될 수 있음을 지정. 즉 복제가 가능한 객체임을 의미
  * Map<E> : 맵의 기본 메소드 지정

### HashMap 생성자
> HashMap에 담을 데이터의 개수가 많은 경우에는 초기 크기를 지정해 주는 것을 권장   
> **HashMap의 키는 기본 자료형과 참조 자료형 모두 가능함.**
* HashMap()
  > 16개의 저장 공간을 갖는 HashMap객체를 생성
* HashMap(int initialCapacity)
  > 매개 변수만큼의 저장 공간을 갖는 HashMap 객체를 생성한다
* HashMap(int initialCapacity, float loadFactor)
  > 첫 매개 변수의 저장 공간을 갖고, 두번재 매개변수의 로드 팩터를 갖는 HashMap 객체를 생성
* HashMap(Map<? extends K,? extends V>m)
  > 매개변수로 넘어온 Map을 구현한 객체에 있는 데이터를 갖는 HashMap객체를 생성

### HashMap 특징
* HashMap의 키는 보통은 int나 long과 같은 숫자나 String 클래스를 키로 많이 사용.
* 어떤 클래스를 만들어 **그 클래스를 키로 사용할 때에는 Object클래스의 hashCode()메소드와 equals()메소드를 잘 구현해 놓아야만 함.**
* HashMap에 객체가 들어가면 hashCode()메소드의 결과 값에 따른 **버켓이라는 목록 형태의 바구니**가 만들어짐.
* 만일 다른 키가 저장되었는데, hashCode()메소드의 결과가 동일하다면 이 버켓에 여러 개의값이 들어갈 수 있다.
* get()메소드가 호출되면 hashCode()의 결과를 확인하고 버켓에 들어간 목록에 데이터가 여러개일 경우 equals()메소드를 호출하여   
  동일한 값을 찾게 됨.
* 키가 되는 객체를 직접 작성할 때에 hashCode()와 equals()를 자동으로 생성해주는 기능을 사용하여 해당 메소드를 구현해야만 한다.
* **map에서는 존재하지 않는 키로 get()을 할 때에는 예외를 발생시키지 않고, null리턴**
  
### TreeMap
> HashMap 객체의 키를 정렬하려면 Arrays클래스를 사용하는 것이지만 불필요한 객체가 생긴다는 단점이 있다.
> 이러한 단점을 보환하는 클래스가 TreeMap이며, 저장하면서 키를 정렬한다.
> 정렬 순서는 숫자 > 알파벳 대문자 > 알파벳 소문자 > 한글 순이다.
> 객체가 저장되거나, 숫자가 저장될 때에는 그 순서가 달라짐
* 너무 많은 데이터를 TreepMap을 이용하여 보관하여 처리할 때에는 HashMap보다는 느림
* TreeMap이 키를 정렬하는 것은 SortedMap이라는 인터페이스를 구현했기 때문임.
* SortedMap을 구현한 클래스들은 모두 키가 정렬되어있어야 하며, 특정 위치의 키를 알 수 있는 메소드를 제공해 줌

### Properties는 Map을 구현하였다.
> Properties클래스는 Hashtable을 확장 하였다.
> System클래스에 static으로 선언되어 있는 getProperties()메소드를 호출하면 Properties 타입의 객체를 리턴함.
