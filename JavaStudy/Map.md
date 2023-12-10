# Map 📌
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
  > 키의 목록을 Set타입으로 리턴
* values()
  > 값의 목록을 Collection타입으로 리턴
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
  
