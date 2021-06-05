# DB Transaction

### Transaction 이란 무엇인가?
> 데이터 베이스의 상태를 변화시키기 위해 수행하는 작업 단위

상태를 변화시킨다? -> SQL 질의어를 사용하여 DB에 접근하여 데이터를 가져오거나, 변경하는 모든 작업

> SELECT <br>
INSERT <br>
DELETE <br>
UPDATE

작업 단위 -> 많은 SQL명령 문들을 사람이 정하는 기준에 따라 정하는 것

즉, 하나의 Transaction 설계를 잘 만드는 것이 데이터를 다룰 때 많은 이점을 가져다 준다.

Transaction은 여러 특징이있다.
약자를 줄여서 ACID라고하는데, 하나하나 살펴보자.

### 원자성(Atomicity)
> 트랜잭션이 DB에 모두 반영되거나, 혹은 모두 반영되지 않아야 한다.

### 일관성(Consistency)
> 트랜잭션의 작업 처리 결과는 항상 일관성이 있어야 한다.

### 독립성(Isolation)
> 둘 이상의 트랜잭션이 동시에 병행 실행되고 있을 때, 어떠한 트랜잭션도 다른 트랜잭션 연산에 끼어들 수 없다.

### 지속성(Durability)
> 트랜잭션이 성공적으로 완료 되었으면, 결과는 영구적으로 반영되어야만 한다.


## Commit이란??

하나의 트랜잭션이 성공적으로 끝났고, DB가 일관성있는 상태일 때, 이를 알려주기 위해 사용하는 연산이다.

## Rollback이란?

하나의 트랜잭션 처리가 비정상적으로 종료되어 원자성이 깨진 경우
트랜잭션이 정상적으로 종료되지 않았을 때, last consistent state로 rooll back 할 수 있음!

### Transaction 관리를 위한 DBMS 전략

이해를 위한 두가지 개념 : DBMS의 구조 / Buffer 관리 정책

1. DBMS의 구조
> 크게 2가지 : Query Processor, Storage System <br>
입출력 단위 : 고정 길이의 page단위로 disk에 읽거나 쓴다. <br>
저장공간 : 비휘발성 저장공간인 DISK에 저장한다. 일부분만 RAM에 저장

2. Page Buffer Manager or Buffer Manager
DBMS의 Storage System에 속하는 모듈중 하나로, Main Memory 에 유지하는 페이지를 관리하는 모듈이다.
> Buffer 관리 정책에 따라, UNDO 복구와 REDO 복구가 요구되거나, 그렇지 않게 되므로 Transaction 관리에 매우 중요한 결정을 가져온다.

3. UNDO
필요한 이유 : 수정된 페이지들이 **Buffer 교체 알고리즘에 따라서 디스크에 출력** 될수 있음. Buffer 교체는 Transaction과는 무관하게, Buffer 상태에 따라서 결정이 된다. 이로인하여, 정상적으로 종료되지 않은 transaction이 변경한 page들은 원상 복구 되어야 하는데, 이러한 복구를 UNDO라고 함

- 2개의 정책 steal : 수정된 페이지를 언제든지 디스크에 쓸 수 있는 정책
    - 대부분의 RDBMS가 채택하는 버퍼 관리 정책
    - UNDO Logging과 복구를 필요로 함
4. REDO
이미 commit한 Transaction의 수정을 재 반영 하는 복구 작업
버퍼 관리 정책에 영향을 받음
- Transaction이 종료되는 시점에 해당 Transaction이 수정한 page를 디스크에 쓸 것인지, 아닌지의 기준을 가진다.

