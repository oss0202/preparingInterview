### 트랜잭션( Transaction )
- 데이터베이스의 상태를 변환시키는 하나의 논리적인 기능을 수행하기 위한 작업의 단위
- 특징
  - **원자성(Atomicity)** 
    - 트랜잭션의 작업이 부분적으로 실행되거나 중단되지 않는 것을 보장
  - **일관성(Consistency)**
    - 트랜잭션이 성공적으로 완료되면 일관적인 DB상태를 유지하도록 보장
  - **독립성(Isolation)**
    - 트랜잭션 수행시 다른 트랜잭션의 작업이 끼어들지 못하도록 보장
  - **지속성(Duration)**
    - 성공적으로 수행된 트랜잭션은 영원히 반영되는 것을 보장

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
- **효율적인 INDEX**
  - WHERE 절에 자주 등장하는 컬럼을 인덱스로 설정
  - ORDER BY 절에 자주 등장하는 컬럼을 인덱스로 설정
  - SELECT 절에 자주 등장하는 컬럼들을 잘 조합해서 인덱스로 구성
  - JOIN이 자주 사용되는 열에 인덱스를 생성
- **데이터의 중복도**
  - 중복도가 높다. = 분포도가 낮다. = Cardinality가 낮다. = 나타나는 데이터의 종류가 별로 없다.
  - 중복도가 낮다. = 분포도가 높다. = Cardinality가 높다. = 나타나는 데이터의 종류가 많다.
  - 중복도가 높고 분포도가 낮을 경우 모든 ROW를 검색하는 table full scan이 더 나을수도 있다.
  따라서 중복도가 낮은 컬럼을 인덱스로 잡아야 한다.
- **인덱스가 안 되는 쿼리**
  - 컬럼을 가공
    - ex. WHERE SUBSTR(ORDER_NO, 1,4) = ‘2021’ -> WHERE ORDER_NO LIKE ‘2021%’
  - 인덱스 컬럼의 묵시적 형변환(같은 타입으로 비교해야함)
    - ex) WHERE REG_DATE = ‘20211224’ -> WHERE REG_DATE = TO_DATE(‘20211124’, ‘YYYYMMDD’)
  - 인덕스 컬럼 부정형 비교
    - ex) WHERE MEM_TYPE != ‘10’ -> WHERE MEM_TYPE IN(‘20’, ‘30’)
  - %가 앞에 위치
    - or 조건 사용 -> UNION ALL로 대체
- **주의점**
  - SELECT가 자주 사용되는 테이블이라면 성능 향상의 효과를 기대할 수 있지만,
UPDATE, DELETE, INSERT 쿼리가 자주 사용되는 테이블이라면 오히려 성능이 감소할 수 있다.
  - 테이블에만 insert하는게 아니라 index에도 insert해야 해서 느려진다.
  - 손익분기점
    - 테이블이 가지고 있는 전체 데이터양의 10 ~ 15%이내의 데이터가 출력 될 때만 INDEX를 타는게 효율적이다.
  
### UNION
- 여러개의 SQL문을 합쳐 하나의 SQL문으로 만들어 준다.
- UNION : 두 쿼리의 결과에서 중복되는 값을 삭제하여 나타낸다.
- UNION ALL : 두 쿼리의 결과에서 중복되는 값을 모두 보여준다.