# Set 📌
> 순서에 상관 없이, 어떤 데이터가 존재하는지를 확인하기 위한 용도로 사용함     
> 중복되는 것을 방지하고, 원하는 값이 포함되어 있는지를 확인하는 것이 주 용도임.      
> 보관되어 있는 순서가 전혀 중요하지 않을 때 사용해야만 함

### Set 인터페이스를 구현한 주요 클래스
* HashSet
  > 순서가 전혀 필요 없는 데이터를 해시테이블에 저장한다. Set중 가장 성능이 좋다.
* TreeSet
  > 저장된 데이터의 값에 따라서 정렬되는 셋. red-black이라는 트리 타입으로 값이 저장되며,
  > HashSet보다 성능이 약간 느림
* LinkedHashSet
  > 연결 된 목록 타입으로 구현된 해시테이블에 데이터를 저장. 저장된 순서에 따라 값이 정렬되며,
  > 세가지 Set중 가장 성능이 나쁨

### HashSet
* HashSet의 상속관계
  * **java.lang.Object > java.util.AbstractCollection<E> > java.util.AbstractSet<E> > java.util.HashSet<E>**
* HashSet가 구현한 인터페이스
  * **Serializable, Cloneable, Iterable, Collection, Set**
    * Serializable : 원격으로 객체를 전송하거나, 파일에 저장할 수 있음을 지정
    * Cloneable : Object 클래스의 colne() 메소드가 제대로 수행될 수 있음을 지정. 즉 복제가 가능한 객체임을 의미
    * Iterable<E> : 객체가 "foreach" 문장을 사용할 수 있음을 지정
    * Collection<E> : 여러개의 객체를 하나의 객체에 담아 처리할 때의 메소드 지정
    * Set<E> : 셋 데이터를 처리하는 것과 관련된 메소드 저장

### HashSet 생성자
* HashSet()
  > 16개의 공간과 0.75의 로드팩터를 갖는 객체 생성
* HashSet(Collection<? extends E> c)
  > 매개변수로 받은 컬랙션 객체의 데이터를 HashSet에 담음
* HashSet(int initialcapacity)
  > 매개변수로 받은 개수만큼 데이터 저장공간과 0.75의 로드팩터를 갖는 객체 생성
* HashSet(int initialcapacity, float loadFactor)
  > 매개변수의 개수만큼의 데이터 저장공간과 두번째 매개변수 만큼의 로드팩터를 갖는 객체 생성

### 로드팩터(load factor)
> (데이터의 개수) / (저장 공간)을 의미함.
> 데이터의 개수가 증가하여 로드 팩터보다 커지면, 저장공간의 크기는 증가되고 해시 재정리 작업을 해야하며,
> 데이터가 해시 재정리 작업에 들어가면, 내부에 갖고 있는 자료구조를 다시 생성하는 단계를 거쳐야 하므로 성능에 영향 발생.
  * 로드팩터가 클 수록 공간은 넉넉해지지만, 데이터를 찾는 시간은 증가함
  * 초기 공간 개수와 로드팩터는 데이터의 크기를 고려하여 산정하는 것이 좋음
  * 초기크기가 (데이터의 개수)/(로드 팩터) 보다 클 경우에는 데이터를 쉽게 찾기 위한 해시 재정리 작업이 발생하지 않음.

### HashSet의 주요 메소드
* add(E e)
  > 데이터 추가
* clear()
  > 모든 데이터 삭제
* clone()
  > HashSet 객체 복제하지만 안에 담겨있는 데이터는 복제하지 않음
* contains(Object o)
  > 지정한 객체가 존재하는지 확인
* isEmpty()
  > 데이터가 있는지 확인
* iterator()
  > 데이터를 꺼내기 위한 Iterator 객체 리턴
* remove(Object o)
  > 매개변수로 넘어온 객체를 삭제
* size()
  > 데이터 개수 리턴

