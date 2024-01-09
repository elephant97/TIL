# Mysql 트랜잭션 격리수준

### 트랜잭션의 격리수준 (Transaction Isolation Level)
> 트랜잭션의 격리수준이란, 어떤 트랜잭션이 동시에 처리될 떄 특정 트랜잭션이 다른 트랜잭션에서 변경하거나 조회하는 데이터를      
> 볼 수 있게 허용할지 여부를 결정하는 것
* 트랜잭션의 격리 수준의 격리(고립)가 높은 수준은 아래의 순서와 같다(위에서부터 높은 순서이며, Auto Commit=false인 상태에서 발생)
  * SERIALIZABLE
  * REPEATABLE READ
  * READ COMMITED
  * READ UNCOMMITED

### Mysql 읽기/쓰기 Lock
* 

### SERIALIZABLE
> 가장 엄격한 격리 수준으로, 이름 그대로 트랜잭션을 순차적으로 진행함
* SERIALIZABLE에서 여러 트랜잭션이 동일한 레코드에 동시 접근할 수 없으므로, 어떠한 데이터 부정합 문제도 발생하지 않음
* 하지만 트랜잭션이 순차적으로 처리되어야 하므로 동시 처리 성능이 매우 떨어짐
* 
