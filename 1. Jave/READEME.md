### Java Generic 이란?
- 클래스 내부에 사용할 데이터 타입을 인스턴스 생성 시에 결정하는 방식입니다.
- 컴파일할 때 타입체크를해서 사전에 에러를 잡을 수 있다.
- 코드의 재사용성이 좋아진다.
### Java Reflection 이란?
- JVM에서 실행되는 애플리케이션의 런타임 동작을 검사하거나 수정하는 기능이 필요한 프로그램에서 사용됩니다.
- 클래스의 타입을 알지 못해도 그 클래스의 메서드, 타입, 변수 등을 접근할 수 있도록 해주는 API입니다.
- 대표적으로 ORM기술인 하이버네이트, jackson라이브러리 등에 사용됩니다.

### Exception 이란?
- 예외(Exception) : 정상적인 프로그램의 흐름에 어긋나는 것
- 에러(Error) : 시스템에 무엇인가 비정상적인 상황이 발생하는 경우
  - ex. OutOfMemory, StackOverflowError, ...

### Exception 종류
  |구분|Checked Exception|Unchecked Exception|
  |:------:|:---|:---|
  |확인 시점|**컴파일(Compile)** 시점|**런타임(Runtime)** 시점|
  |처리 여부|반드시 예외 처리|명시적으로 안해도 됨|
  |트랜잭션 처리|**예외 발생시 롤백(rollback)X**|**예외 발생 시 롤백**|
  |종류|IOException, ClassNotFoundException|NullPointException, ClassCastException 등|

### Checked Exception rollback 방법
- try~catch
- Transactional의 rollbackFor 옵션 사용
- 컴파일 단계에서 체크
- Spring에서는 jdbcTemplate에서 unChecked Exception으로 포장해서 리턴해줘서 rollback 된다. 

### Exception을 만들어서 사용해본적?
- Filter
  - Post나 Put일 때 Body가 비었을 때 발생(custom Exception)
  - Http Request Method를 올바르게 요청하지 않았을 경우 발생(HttpRequestMethodNotSupportedException)
  
### Stream 이란?

### Stream 장단점

### Steam 구성

### Entity equals 메소드 재정의 기준(해시코드 오버라이드)

### HashMap에서 충돌(collision)을 회피하기 위한 방법은?

### jvm의 종류

