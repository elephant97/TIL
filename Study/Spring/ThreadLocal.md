# ThreadLocal 
김영한님 Spring 핵심원리 - 고급편

<br>

### Thread local
> 쓰레드 로컬을 사용하면 각 쓰레드 마다 별도의 내부 저장소를 제공한다.     
> 따라서 같은 인스턴스의 쓰레드 로컬 필드에 접근해도 문제가 없다.

### Thread Local 사용법
* 값 저장: `ThreadLocal.set(xxx)`
* 값 조회: `ThreadLocal.get()`
* 값 제거: `ThreadLocal.remove()`
* **해당 쓰레드가 쓰레드 로컬을 모두 사용하고 나면 `ThreadLocal.remove()` 를 호출해서 쓰레드 로컬에 저장 된 값을 제거해주어야 함**
