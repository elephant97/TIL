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

### ThreadLocal 사용시 주의사항
> 쓰레드 로컬의 값을 사용 후 제거하지 않고 그냥 두는 경우 WAS(톱캣)처럼 쓰레드 풀을 사용하는 경우에 심각한 문제가 발생할 수 있다.
* 쓰레드 풀은 풀에 있는 쓰레드를 계속 재 사용 하기 때문에 다음 요청에서 같은 쓰레드가 반환 되었을 시 데이터가 잘못 조회되는 버그를 초래할 수 있음