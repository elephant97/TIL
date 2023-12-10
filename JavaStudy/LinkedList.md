# LinkedList 📌
> 배열의 중간에 있는 데이터가 지속적으로 삭제되고, 추가될 경우 LinkedList가 배열보다 메모리 공간 측변에서 훨씬 유리함.
> LinkedList는 List인터페이스 뿐만 아니라 Queue와 Deque(Double Ended Queue) 인터페이스도 구현하고 있어,
> List이면서, Queue와 Deque도 된다.

### LinkedList
* LinkedList의 상속관계
  * **java.lang.Object > java.util.AbstractCollection<E> > java.util.AbstractList<E>**   
    **> java.util.AbstractSequentialList<E> > java.util.LinkedList<E>**
* LinkedList가 구현한 인터페이스
  * **Serializable, Cloneable, Iterable, Collection, Deque, List, Queue**
    * Serializable : 원격으로 객체를 전송하거나, 파일에 저장할 수 있음을 지정
    * Cloneable : Object 클래스의 colne() 메소드가 제대로 수행될 수 있음을 지정. 즉 복제가 가능한 객체임을 의미
    * Iterable<E> : 객체가 "foreach" 문장을 사용할 수 있음을 지정
    * Collection<E> : 여러개의 객체를 하나의 객체에 담아 처리할 때의 메소드 지정
    * Deque<E> : 맨 앞과 맨 뒤의 값을 용이하게 처리하는 큐와 관련된 메소드 지정
    * List<E> : 목록형 데이터를 처리하는 것과 관련된 메소드 지정
    * Queue<E> : 큐를 처리하는 것과 관련된 메소드 지정

### LinkedList 생성자
> LinkedList는 일반적인 배열타입 클래스와 다르게 생성자로 객체를 생성할 때 처음부터 크기를 지정하지 않는다.   
> 각 데이터들이 앞 뒤로 연결되는 구조이기 때문에, 미리 공간을 만들어 놓을 필요가 없는 것
  * LinkedList()
    > 비어있는 LinkedList 객체를 생성
  * LinkedList(Collection<? extends E> c)
    > 매개변수로 받은 컬렉션 객체의 데이터를 LinkedList에 담음

### LinkedList의 메소드
* LinkedList의 메소드에는 앞에서부터 또는 뒤에서부터 데이터를 넣거나 빼거나 찾는 메서드들이 First Last 이름으로 붙어 존재함.
* LinkedList객체를 검색하기 위한 Iterator 객체 중에서는 descendingIterator()을 사용하여 끝에서부터 검색 가능 함
