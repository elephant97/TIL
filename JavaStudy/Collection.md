# 컬렉션(Collection) 📌
> 자바에서 컬렉션은 목록성 데이터를 처리하는 자료구조를 통칭한다.   
> 자료구조(Data Structure)란 어떤 정보를 담는 것을 의미. 하나의 데이터가 아닌 여러 데이터를 담을 때 사용.

### 데이터를 담는 자료구조의 분류
  * 순서가 있는 목록형 (List)
  * 순서가 중요하지 않은 셋형 (Set)
  * 먼저 들어온 것이 먼저 나가는 큐형 (Queue)
  * 키-값(Key-Value)으로 저장되는 맵형 (Map) - 유일하게 Collection과 관련 없는 별도의 인터페이스로 선언되어 있음.

### Collection인터페이스를 구현하는 자료구조
> 자바에서는 목록과 셋 큐는 Collection이라는 인터페이스를 구현하고 있다.
> Collection 인터페이스는 java.util 패키지에 선언되어 있으며, 여러개의 객체를 하나의 객체에 담아 처리할 때
> 공통으로 사용하는 여러 메소드들을 선언해 놓았다.

### Collection 인터페이스 
> Collection 인터페이스는 Iterable<E>라는 인터페이스를 확장함.   
> Iterable를 확장했다는 의미는 **인터페이스를 사용하여 데이터를 순차적으로 가져올 수 있다는 의미**
```java
public interface Collection<E> extends Iterable<E>
```
  * 주요 메소드
    * add(E e) : 요소를 추가한다.
    * addAll(Collection) : 매개 변수로 넘어온 컬렉션의 모든 요소를 추가
    * clear() : 컬렉션에 있는 모든 요소 데이터를 지움
    * contains(Object) : 매개 변수로 넘어온 객체가 해당 컬랙션에 있는지 확인하며, 있으면 true 리턴
    * containsAll(Collection) : 매개 변수로 넘어온 객체들이 해당 컬렉션에 있는지 확인하며, 컬렉션에 있는 요소들과 동일한 값이 있을 시 true 리턴
    * equals(Object) : 매개변수로 넘어온 객체와 같은 객체인지 확인
    * hashCode() : 해시코드값 리턴
    * isEmpty() : 컬렉션이 비었는지 확인 비어있으면 true 리턴
    * iterator() : 데이터를 한 건씩 처리하기 위한 Iterator 객체를 리턴
    * remove(Object) : 매개변수와 동일한 객체 삭제
    * removeAll(Collection) : 매개변수로 넘어온 객체들을 해당 컬렉션에서 삭제
    * retailAll(Collection) : 매개변수로 넘어온 객체들만을 컬렉션에 남겨 둠
    * size() : 요소의 개수 리턴
    * toArray() : 컬렉션에 있는 데이터들을 배열로 복사
    * toArray(T[]) : 컬렉션에 있는 데이터들을 지정한 타입의 배열로 복사

### Iterable 인터페이스
* 리턴타입: Iterator<T>
  * Iterator라는 인터페이스의 메소드
      * hasNext() : 추가 데이터가 있는지 확인
      * next() : 현재 위치를 다음 요소로 넘기고 그 값을 리턴함
      * remove() : 데이터 삭제
* 메소드 이름 및 매개변수: iterator()
