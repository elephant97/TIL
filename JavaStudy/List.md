# List 📌
> "목록"은 List 인터페이스로부터 시작되며, List 인터페이스는 Collection 인터페이스를 확장함.   
> 몇몇 추가된 메소드를 제외하고는 Collection에 선언된 메소드와 큰 차이가 없음.   
> **Collection을 확장한 다른 인터페이스와 List 인터페이스의 가장 큰 차이점은 배열처럼 "순서"가 있다는 것**

### List 인터페이스
  * List인터페이스를 구현한 클래스 중 java.util 패키지에서 **ArrayList, Vector, Stack, LinkedList**를 많이 사용함
  * ArrayList와 Vector 클래스의 사용법은 거의동일하고 기능도 거의 비슷함. 두 클래스는 **확장 가능한 배열**이라고 생각하면 된다.
  * Vector는 JDK 1.0부터 있었고, ArrayList는 JDK 1.2dptj cnrk ehla
  * **ArrayList는 Not Thread Safe, Vector는 Thread safe하다.**
  * stack이라는 클래스는 **LIFO**를 지원하기 위하여 Vector를 확장하여 만듬
  * 스택이라는 의미는 보통 메소드가 호출된 순서를 기억하는 장소를 말함.
  * **LinkedList** 클래스는 **"목록"에서도 속하지만, "큐"에도 속함**

### ArrayList
  * ArrayList의 상속관계
    * **java.lang.Object > java.util.AbstractCollection<E> > java.util.AbstractList<E> > java.util.ArrayList<E>**
    * AbstractCollection은 Collection 인터페이스 중 일부 공통적인 메소드를 구현해 놓은 것
    * AbstractList는 List 인터페이스 중 일부 공통적인 메소드를 구현해 놓은 것
  * ArrayList가 구현한 인터페이스
    * **Serializable, Cloneable, Iterable<E>, Collection<E>, List<E>, RandomAccess**
      * Serializable : 원격으로 객체를 전송하거나, 파일에 저장할 수 있음을 지정
      * Cloneable : Object 클래스의 colne() 메소드가 제대로 수행될 수 있음을 지정. 즉 복제가 가능한 객체임을 의미
      * Iterable<E> : 객체가 "foreach" 문장을 사용할 수 있음을 지정
      * Collection<E> : 여러개의 객체를 하나의 객체에 담아 처리할 때의 메소드 지정
      * List<E> : 목록형 데이터를 처리하는 것과 관련된 메소드 지정
      * RandomAccess : 목록형 데이터에 보다 빠르게 접근할 수 있도록 임의로 접근하는 알고리즘 적용된다는 것을 지정

### ArrayList의 생성자
> ArrayList는 서로 다른 종류의 객체를 넣을 순 있으나, 그렇게 사용하지 않고 여러 종류를 하나의 객체에 담을 때에는   
> 되도록이면 DTO라는 객체를 하나 만들어서 담는 것이 좋다.   
> 초기 크기는 10이며, 10개 이상의 데이터가 들어가면 **크기를 늘리는 작업이 ArrayList 내부에서 자동으로 수행 됨**   
> **ArrayList 크기를 늘리는 작업이 수행되면, 애플리케이션 성능에 영향을 주게 되므로 저장되는 데이터의 크기가**   
> **예측 가능하다면 예측 가능한 초기크기를 지정하는 것을 권장함**
```java
ArrayList<String> list = new ArrayList<String>(); //JDK 7부터는 타입을 따로 적지 않고 <>로만 사용 가능
```
* ArrayList()
  > 객체를 저장할 공간이 **10개**인 ArrayList를 만듬
* ArrayList(Collection<? extends E> c)
  > 매개변수로 넘어온 컬렉션 객체가 저장되어 있는 ArrayList를 만듬
* ArrayList(int initialCapacity)
  > 매개 변수로 넘어온 initialCapacity 개수만큼의 저장 공간을 갖는 ArrayList를 만듬

### ArrayList에 데이터 add
> 하나의 데이터를 담을 때에는 add() 메소드를, Collection을 구현한 객체를 한꺼번에 담을 때에는 addAll()메소드를 사용하면 됨.    
> **배열을 복사할 때에는 arraycopy()를 이용하면 Deep copy 처리 가능**   
> Collection관련 객체를 복사할 일이 있을 때에는 생성자를 이용하거나, addAll() 메소드를 사용할 것
* add(E e)
  > 매개변수로 넘어온 데이터를 **가장 끝**에 담음
* add(int index, E e)
  > 매개변수로 넘어온 데이터를 지정된 idex 위치에 담음
  > **이 경우에는 기존 데이터들의 위치가 하나씩 뒤로 밀려남**
* addAll(Collection<? extends E> c)
  > 매개변수로 넘어온 컬렉션 데이터를 가장 끝에 담음
* addAll(int index, Collection<? extends E> c)
  > 매개변수로 넘어온 컬렉션 데이터를 index에 지정된 위치부터 담음

### ArrayList에서 데이터 꺼내기
> ArrayList 객체에 들어가 있는 데이터의 개수는 size()메소드를 통해 알 수 있다.   
> ArrayList의 저장 공간이 아닌 들어가있는 데이터의 개수를 의미한다.   
> **ArrayList는 중복된 데이터를 넣을 수 있음**
* size()
  > 데이터의 개수 리턴
* get(int index)
  > 지정한 위치에 있는 데이터 리턴
* indexOf(Object o)
  > 객체와 동일한 데이터의 위치리턴   
  > 앞에서 부터 찾을 때 사용
* lastIndexOf(Object o)
  > 객체와 동일한 마지막 데이터의 위치 리턴
  > 뒤에서 부터 찾을 때 사용
* toArray()
  > ArrayList 객체에 있는 값들을 Object[] 타입의 배열로 만듬
* toArray(T[] a)
  > ArrayList 객체에 있는 값들을 매개 변수로 넘어온 T 타입의 배열로 만듬   
  > 의미 없이 타입만을 지정하기 위해서 사용할 수도 있음.   
  > ArrayList의 객체의 데이터 크가가 매개변수로 넘어간 배열 객체의 크가보다 클 경우에는 매개변수로 배열이 모든 값이   
  > null로 채워지므로 ArrayList의 size()를 통해 정확한 사이즈 만큼 배열을 선언하는 것이 좋음

### ArrayList 데이터 삭제
* clear()
  > 모든 데이터 삭제
* remove(int index)
  > 지정한 위치에 있는데이터 삭제하고, 삭제한 데이터 리턴함.
* remove(Object o)
  > 해당 객체와 동일한 **첫번째 데이터를만** 삭제함
* removeAll(Collection<?> c)
  > 해당 컬렉션 객체에 있는 데이터와 동일한 **모든 데이터** 삭제

### ArrayList 값 변경
* set(int Index, E element)
  > 지정한 위치에 있는 데이터를 두 번째 매개변수로 넘긴 값으로 변경
  > 해당 위치에 있던 데이터는 리턴 됨
* trimToSize()
  > 객체 공간의 크기를 데이터의 개수만큼 변경함
  > 저장할 수 있는 공간은 만들어 두었지만, 데이터가 저장되어 있지 않을 때 해당 공간을 없앰    
  > 만일 ArrayList의 객체를 원격으로 전송하거나, 파일로 저장하는 일이 없을 때 이 메소드 호출로 데이터 크기를 줄일 수 있는 장점이 있음.

### ArrayList를 Thread safe하게 만드는 법
> ArrayList는 Thread safe하지 않으므로 쓰레드에서 안전한 객체로 만들려면 다음과 같이 선언해야함
```java
List list = Collection.synchronizedList(new ArrayList(...));
```

### Stack 클래스
> LIFO(후입선출)기능을 구현하려고 할 때 필요한 클래스.
> Stack보다 더 빠른 **ArrayDeque**라는 클래스가 존재하지만 이 클래스는 쓰레드에 안전하지 못함.
* Stack 클래스의 상속관계
  * **java.lang.Object > java.util.AbstractCollection<E> > java.util.AbstractList<E> > java.util.Vector<E> > java.util.Stack<E>**
* Stack 클래스에서 구현한 인터페이스
  * **Serializable, Cloneable, Iterable<E>, Collection<E>, List<E>, RandomAccess**

### Stack 생성자
* stack() : 아무 데이터도 없는 Stack 객체를 만듬

### Stack 메소드
* empty() : 객체가 비어있는 지를 확인
* peek() : 객체의 가장 위에 있는 데이터를 리턴함
* pop() : 객체의 가장 위에 있는 데이터를 지우고 리턴
* push(E item) : 매개변수로 넘어온 데이터를 가장 위에 저장
* search(Object o) : 매개변수로 넘어온 데이터의 위치 리턴
