### 트랜잭션( Transaction )
- 데이터베이스의 상태를 변환시키는 하나의 논리적인 기능을 수행하기 위한 작업의 단위
- 특징
  - 원자성(Atomicity) 
  - 일관성(Consistency)
  - 독립성(Isolation)
  - 지속성(Duration)

### Transaction isolation
- 동시에 여러 트랜잭션이 처리될 때 특정 트랜잭션이 다른 트랜잭션에서
변경되거나 조회하는 데이터를 볼 수 있도록 허용할지 말지를 결정하는 것
- 수준(Level)
  - **Read Uncommitted**
    - SELECT 쿼리 실행시에 다른 트랜잭션에서 COMMIT 되지 않은 데이터를 읽어올 수 있습니다.
    - COMMIT 되지 않은 데이터를 읽는 현상을 Dirty read라고 한다.
    - *INSERT만 진행되고 ROLLBACK 될 수도 있는, 즉 한번도 COMMIT 되지 않은 데이터를 읽을 수 있어 유의해야한다.*
  - **Read Committed**
    - RDB에서 대부분 기본적으로 사용되고 있는 격리 수준이다.
    - COMMIT이 완료된 데이터만 SELECT시에 보이는 수준을 보장한다.
    - *나의 트랜잭션 안에서 SELECT를 수행 할 때마다 데이터가 동일하다는 보장을 해주지 않는다.*
  - **Repeatable Read**
    - 처음으로 SELECT를 수행한 시간을기록한 뒤 그 이후에는 모든 SELECT 마다 해당 시점을 기준으로 Consistent Read를 수행한다.
    - Consistent Read : Read(SELECT) opration을 수행할 때 현재 DB의 값이 아닌 특정 시점의 DB snapshot을 읽어오는 것이다.
  - **Serializable**
    - 모든 작업을 하나의 트랜잭션에서 처리하는 것과 같은 가장 높은 고립수준을 제공한다.

### 인덱스( Index )
- 테이블의 동작 속도(Row 검색 속도)를 높여주는 자료구조
- 주의점
  - SELECT가 자주 사용되는 테이블이라면 성능 향상의 효과를 기대할 수 있지만,
UPDATE, DELETE, INSERT 쿼리가 자주 사용되는 테이블이라면 오히려 성능이 감소할 수 있다.
  - 카디널리티가 높은(컬럼에 중복되는 값이 많은 컬럼)을 인덱스로 걸어야 한다. 카디널리티가 낮은 
  컬럼을 인덱스로 사용시 수많은 row가 검색 될 것이며, 다시 Full Search로써 결과를 검색해야한다.
  