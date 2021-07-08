# Transaction의 이것저것

## Propagation Behavior

Method 호출자와 호출된 method에 대해 트랜잭션의 범위를 설정한다.

+ **PROPAGATION_REQUIRED** (default)
  + Method가 반드시 트랜잭션 내에서 실행돼야 함을 의미함.
  + 만일 현재 진행 중인 트랜잭션이 존재하면 method가 그 트랜잭션 내에서 실행되고, 그렇지 않으면 새로운 트랜잭션을 시작함.
  
  <br>
+ **PROPAGATION_SUPPORTS**
  
  + Method가 트랜잭션을 필요로 하지는 않지만, 만일 진행 중인 트랜잭션이 존재하면 그 트랜잭션 내에서 실행됨.
  
  <br>
+ **PROPAGATION_MANDATORY**
  
  + Method가 반드시 트랜잭션 내에서 실행돼야 함을 의미함.
  + 만일 현재 진행 중인 트랜잭션이 존재하지 않으면 예외(exception)을 발생시킴.
  
  <br>
+ **PROPAGATION_REQUIRES_NEW**
  
  + Method가 반드시 자기 자신의 트랜잭션 내에서 실행돼야 함을 의미함.
  + 항상 새로운 트랜잭션을 시작함.
  + 만일 현재 진행 중인 트랜잭션이 존재하면 그 트랜잭션은 일시 중지되고 새로운 트랜잭션이 종료된 후에 다시 실행됨
  
  <br>
+ **PROPAGATION_NOT_SUPPORTED**
  
  + Method가 트랜잭션으로 실행될 필요가 없음을 의미함.
  + 만일 현재 진행 중인 트랜잭션이 존재하면 그 트랜잭션은 일시 중지되고 method가 종료된 후에 다시 실행됨
  
  <br>
+ **PROPAGATION_NEVER**
  
  + Method가 트랜잭션으로 실행되지 않아야 함을 의미함.
  + 만일 현재 진행 중인 트랜잭션이 존재하면 예외(exception)을 발생시킴
  
  <br>
+ **PROPAGATION_NESTED**
  
  + 현재 진행 중인 트랜잭션이 존재하면 method가 중첩 트랜잭션(nested transaction)으로 실행돼야 함을 의미함.  (중첩 트랜잭션은 외부 트랜잭션과 독립적으로 commit 또는 rollback될 수 있음)
  + 만일 진행 중인 트랜잭션이 존재하지 않으면 새로운 트랜잭션을 시작함.

<br>

## Isolation Level

한 트랜잭션이 동시에 실행 중인 다른 트랜잭션의 영향을 얼마나 받는가를 의미한다. 트랜잭션들의 동시성과 성능을 결정시킨다. 예를 들어 동시성을 높이면 성능이 올라간다.

+ **Dirty reads**
  + 다른 트랜잭션에 의해 변경됐지만 아직 commit 되지 않은 데이터를 읽는 현상
  + 데이터를 변경한 트랜잭션이 rollback되는 경우 문제가 발생한다.
+ **Non-repeatable reads**
  + 같은 질의를 두 번 이상 실행할 때 서로 다른 데이터를 얻는 현상
  + 두 질의 사이에 다른 트랜잭션이 데이터를 변경하고 commit 한 경우
+ **Phantom reads**
  + 여러 데이터 행을 읽은 후 다시 질의를 수행할 때 이전에 없던 데이터 행들을 얻는 현상
  + 동시 실행 중인 다른 트랜잭션이 새로운 행을 삽입한 경우

<br>

### Isolation levels

+ **ISOLATION_DEFAULT**

  +  이용하는 data source의 default 값을 사용
  +  ex) ISOLATION_READ_COMMITTED in Oracle

  <br>

+ **ISOLATION_READ_UNCOMMITTED**
  
  + 동시 실행 중인 다른 트랜잭션이 commit하지 않은 데이터를 읽는 것을 허용함
  + Dirty reads, phantom reads, non-repeatable reads가 발생할 수 있음
  
  <br>
  
+ **ISOLATION_READ_UNCOMMITTED**
  
  + Oracle의 default
  + 동시 실행 중인 다른 트랜잭션이 commit한 데이터만 읽는 것을 허용함
  + Dirty reads는 방지할 수 있으나 phantom reads와 non-repeatable reads는 발생 가능
  
  <br>
  
+ **ISOLATION_REPEATABLE_READ**
  
  + 같은 데이터에 대한 여러 번의 read가 동일한 결과를 얻음을 보장함.
  + Dirty reads와 non-repeatable reads를 방지할 수 있으나 phantom reads는 발생 가능
  
  <br>
  
+ **ISOLATION_SERIALIZABLE**
  
  + 완전한 ACID-compliant isolation level을 의미한다.
  + Dirty reads와 non-repeatable reads, phantom reads를 모두 방지할 수 있음
  + 일반적으로 트랜잭션에서 접근하는 모든 테이블들에 대해 full table lock을 생성하므로 트랜잭션의 실행 속도가 가장 느림.

