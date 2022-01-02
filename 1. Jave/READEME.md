### 객체지향이란
- 객체 간의 상호작용을 통해 로직을 구성하는 프로그래밍 방법이다.

### 절차지향, 객체지향 프로그래밍 비교
|구분|**절차지향**|**객체지향**|
  |:------:|:---|:---|
|장점|- 컴퓨터의 처리구조와 유사해 실행속도가 빠름|- 코드재활용성이 높음<br>- 유지보수가 쉽다.
|단점|- 유지보수가 어렵다.<br>- 대규모 협업프로젝트 부적합 | - 처리속도가 상대적으로 느림<br>- 설계에 많은 시간과 노력이 소요<br>- 대규모 협업 프로젝트에 적합

### 객체지향 특징
- **추상화(Abstraction)**
  - 객체의 기능 자체에 중점을 준다. 
  - 클래스 구현 세부 사항과 동작을 분리하는 것이 목표이다.
- **캡슐화(Encapsulation)**
  - 객체의 동작구현에 중점을 둔다.
  - 객체가 내부적으로 기능을 어떻게 구현했는지 감추는 것
  - 내부 구현에 대한 유연함을 제공해 준다.
- **상속(Inheritance)**
  - 재사용을 목적으로, 상위 개념의 특징을 하위 개념이 물려받는 것
- **다형성(Polymorphism)**
  - 같은 모양의 함수가 상황에 따라 다르게 동작 하는 것
  - 오버로딩(Overloading) : 메서드의 이름은 같고 매개변수의 갯수나 타입이 다른 함수를 정의(리턴값은 상관없음) 
  - 오버라이딩(Overriding) : 상위 클래스가 가지고 있는 메서드를 하위 클래스가 재정의해서 사용

### 객체지향적 설계 원칙
- **SRP(Single Responsibility Principle)** : 하나의 클래스는 하나의 책임을 가져야 한다.
- **OCP(Open-Closed Principle)** : 확장에는 열려있고 수정에는 닫혀있어야 한다.
- **LSP(Liskov Substitution Principle)** : 상위 타입의 객체를 하위 타입의 객체로 치환해도 정상적으로 동작해야 한다.
- **ISP(Interface Segregation Principle)** : 클라이언트는 자신이 이용하지 않는 메서드에 의존하면 안된다.
- **DIP(Dependency Inversion Principle)** : 변화하지 않는 것에 의존하라


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
  |트랜잭션 처리|**예외 발생시 롤백X**|**예외 발생 시 롤백**|
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
- 배열 또는 컬렉션 인스턴스에 함수 여러 개를 조합해서 원하는 결과를 필터링하고 가공된 결과를 얻을 수 있다.
- 병렬처리(multi-threading)가능 (하나의 작업을 둘 이상의 작업으로 잘게 나눠서 동시에 진행)

### Steam 구성
- 생성하기 : 스트림 인스턴스 생성
  - 컬랙션 : 컬랙션.stream();
  - 배열 : Arrays.stream(배열)
- 가공하기 : filtering, mapping 등 원하는 결과를 만들어가는 중간작업
  - 필터링 : filter(), distinct()
  - 변환 : map(), flatMap()
  - 제한 : limit(), skip()
  - 정렬 : sorted()
  - 연산 결과 확인 : peek()
- 결과 만들기 : 최종적으로 결과를 만들어내는 작업
  - 출럭 : foreach()
  - 소모 : reduce()
  - 검색 : findFirst(), findAny()
  - 통계 : count(), min(), max()
  - 연산 : sum(), average()
  - 수집 : collect()

### equals를 재정의한 클래스에서는 hashcode도 재정의 해야한다 그 이유는?
- hashcode를 재정의 하지 않으면 hash를 사용하는 HashMap, HashSet과 같은 컬렉션의 원소로 사용될 때 문제가 발생할 것이다.

### HashMap에서 충돌(collision)을 회피하기 위한 방법은?
- Open Addressing
  - 충돌이 발생하면 다른 해시버킷에 해당 자료를 삽입
- Separate Chaining
  - 충돌 시 해당 버킷값을 첫 부분으로 하는 링크드 리스트로 해결
  
### Garbage Collection의 종류
- GC : Java Runtime시 Heap 영역에 저장되는 객체들은 따로 정리하지 않으면 OutOfMemory Exception이 발생할 수 있다.
이를 방지하기 위하여 JVM에서는 주기적으로 사용하지 않는 객체를 수집하여 정리하는 GC를 진행한다.

