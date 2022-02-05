## 객체지향이란
객체 간의 상호작용을 통해 로직을 구성하는 프로그래밍 방법이다.

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

## Java
### Java 8 주요변경사항
1. 람다표현식(Lamda Expression) : 함수형 프로그래밍이 가능하게 됨
   - 익명 클래스의 한 개의 메소드를 식으로 표현한 것
     - 익명클래스 : 이름이 없는 클래스, 한 개의 객체만을 생성할 수 있는 일회용 클래스
2. 메소드 참조(Method Reference) : 특정 람다식을 축약한 것
3. 스트림 API(Stream API) : 데이터의   흐름 
4. java.time 패키지 : 더 직관적이고 개선된 Data, Time API를 제공
   - 불변 객체가 아니다(not immutable)
     - set으로 변경이 가능하다.
   - int 상수필드의 남용
   - 헷갈리는 월 지정
     - 1월이 0
     - Calendar.OCTOBER의  값은 9( != 10)
   - 일관성 없는 요일 상수
     - Calendar는 일요일이 1
     - Date는 일요일이 0
5. Optional : 값을 Optional로 캡슐화하여 NullPointerException을 막음

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
- Spring에서는 jdbcTemplate에서 unChecked Exception으로 포장해서 리턴해줘서 rollback 된다. 

### Exception을 만들어서 사용해본적?
- Filter
  - Post나 Put일 때 Body가 비었을 때 발생(custom Exception)
  - Http Request Method를 올바르게 요청하지 않았을 경우 발생(HttpRequestMethodNotSupportedException)

### equals를 재정의한 클래스에서는 hashcode도 재정의 해야한다 그 이유는?
- hashcode를 재정의 하지 않으면 hash를 사용하는 HashMap, HashSet과 같은 컬렉션의 원소로 사용될 때 문제가 발생할 것이다.

### HashMap에서 충돌(collision)을 회피하기 위한 방법은?
- Open Addressing
    - 충돌이 발생하면 다른 해시버킷에 해당 자료를 삽입
- Separate Chaining
    - 충돌 시 해당 버킷값을 첫 부분으로 하는 링크드 리스트로 해결

### try-with-resource 를 사용해야 하는 이유
**try()** 에 자원 객체를 선언해 사용하면, try 블록이 끝날 때 해당 자원을 자동으로 종료(**close()**)해준다.
단, 선언된 자원은 ***AutoCloseable 인터페이스***가 구현된 객체여야 한다.

입출력 관련 메소드는 IOException 예외를 throws하는데 이 IOException 예외가 Checked Exception이기 때문에 예외를 try~catch로 
적절히 처리해주거나 throws를 이용해 예외 처리의 책임을 호출하는 쪽으로 처리를 해줘야한다.
```java
public void write(String fileName, String word) throws IOException {
        Writer writer = new FileWriter(fileName);
        writer.write(word);
    }
```
하지만 이렇게 처리할 경우 FileWriter 스트림이 정상적으로 생성된 후 write(word) 메소드를 실행하다가 예외가 발생할 경우 해당 예외가
 정상적으로 throws 되겠지만, 스트림은 소멸하지 못하고 남겨진 채 메소드가 종료된다.

스트림이 메모리에 남아있을 경우 값 유실 문제가 발생할수도 있으므로 스트림을 메모리에서 소멸시켜주는 스트림을 닫는 과정이 필요하다.
```java
public void write(String fileName, String word) throws IOException {
Writer writer = new FileWriter(fileName);
writer.write(word);
writer.close();
}
```
하지만 이렇게 할 경우 write메소드를 실행 도중에 예외가 발생할 경우엔 close메소드가 실행되지 않기 때문에 
Java6까지는 다음과 같은 방법으로 입출력 스트림을 다루었다. 
```java
public void write(String fileName,String word) throws IOException{
	try{
		Writer writer = new FileWriter(fileName);
		writer.write(word);
	}
	finilly{
		writer.close();
	}
}
```
스트림을 닫는 과정에서 예외가 발생할 경우 try 블록에서 발생한 예외가 아니라 finally 블록에서 발생한 예외가 던져진다.
그래서 java 7 부터는 try ~ with ~ resource 라는 문법이 추가되었다.
```java
public void write(String fileName,String word) throws IOException{
	try(Writer writer = new FileWriter(fileName)){
		writer.write(word);
	}
}
```
try 뒤에 오는 괄호안에 try 블록에서 사용할 스트림(리소스)를 생성해주기만 하면 try블록에서 예외가 발생하든 발생하지 않든간에
생성한 리소스를 자동으로 close 해준다.(close 과정에서 발생한 예외도 받을 수 있다.)

## JVM ( Java Virtual Machine )
자바와 운영체제 사이에서 중개자 역할을 수행하며, 자바가 운영체제에 구애받지 않고 프로그램을 실행할 수 있도록 도와준다.
- 구조
    - Class Loader : JVM 내로 클래스 파일을 로드, 런타임 시에 동적으로 클래스를 로드
    - Execution Engine : Class Loader를 통해 JVM 내의 Runtime Data Area에 배치된 바이트 코드들을 명령어 단위로 읽어서 실행
    - Garbage Collector : GC는 힙 메모리 영역에 생성된 객체들 중에서 참조되지 않은 객체들을 탐색 후 제거
    - **Runtime Data Area** : JVM의 메모리 영역
        1) **Method area**
            - 모든 쓰레드가 공유하는 메모리 영역
            - 클래스, 인터페이스, 메소드, 필드, Static 변수 등의 바이트 코드를 보관
        2) **Heap area**
            - 모든 쓰레드가 공유하며, new 키워드로 생성된 객체와 배열이 생성되는 영역
            - GC가 참조되지 않는 메모리를 확인하고 제거하는 영역
        3) **Stack area**
            - 메서드 호출 시 메서드 안에서 사용되는 값들을 저장하고, 호출된 메서드의 매개변수, 지역변수, 리턴 값 및 연산 시 일어나는 값들을 임시로 저장
            - 메서드 수행이 끝나면 프레임별로 삭제
        4) PC Register
            - 쓰레드가 시작될 때 생성되며, 생성될 때마다 생성되는 공간으로 쓰레드마다 하나씩 존재
            - 쓰레드가 어떤 부분을 무슨 명령으로 실행해야할 지에 대한 기록을 하는 부분으로 현재 수행중인 JVM 명령의 주소를 갖음
        5) Native method stack
            - 자바 외 언어로 작성된 네이티브 코드를 위한 메모리 영역

### Garbage Collection의 종류
- GC : Java Runtime시 Heap 영역에 저장되는 객체들은 따로 정리하지 않으면 OutOfMemory Exception이 발생할 수 있다.
  이를 방지하기 위하여 JVM에서는 주기적으로 사용하지 않는 객체를 수집하여 정리하는 GC를 진행한다.

## Stream
### Stream 이란?
- Java8부터 지원하며, 배열, 컬랙션 인스턴스에 함수 여러 개를 조합해서 필터링하여 가공된 결과를 얻을 수 있다.
- 특징
  - 원본 데이터를 변경하지 않고 별도의 Stream을 생성
  - **내부 반복자를 사용하므로 병렬처리(multi-threading)가 가능하다.**
    - 반복문이 코드상에 노출되지 않는다.
      - 외부 반복자 : 개발자가 코드로 직접 컬랙션의 요소를 반복해서 가져오는 코드, 흔히 사용하는 index 반복문, Iterator를 사용한 while문
      - 내부 반복자 : 컬랙션 내부에서 요소들을 반복시키고, 개발자는 요소당 처리해야할 코드만 제공하는 코드 패턴 
  - 장점
    - 가독성이 좋음
    - 병렬처리 가능
  - 단점
    - 디버깅이 힘듬
      - 스트림은 한 번에 수행되기 때문에 처음부터 전부 확인해야 함
    - 재사용 불가능

### Steam 구성
- 생성하기 : 스트림 인스턴스 생성, 재사용이 불가능하므로 닫히면 다시 생성해줘야함
  - 컬랙션 : 컬랙션.stream();
  - 배열 : Arrays.stream(배열)
- 가공하기 : 연산 결과를 Stream으로 다시 반환하기 때문에 연속해서 중간 연산을 이어갈 수 있음
  - 필터링 : filter(), distinct()
  - 변환 : map(), flatMap()
  - 제한 : limit(), skip()
  - 정렬 : sorted()
  - 연산 결과 확인 : peek()
- 결과 만들기 : 최종적으로 결과를 만들어내는 작업, Stream의 요소들을 소모하면서 수행되기 때문에 1번만 처리가능
  - 출력 : foreach()
  - 소모 : reduce()
  - 검색 : findFirst(), findAny()
  - 통계 : count(), min(), max()
  - 연산 : sum(), average()
  - 수집 : collect()
    
## Java 변수유형
| 변수 유형 | 선언 위치 | 사용 범위 | 메모리 | Life Cycle|
|:---:|:---:|:---|:---:|:---|
| 지역 변수 | 함수 내부 | 함수 내부 | static | 한수 호출 시 생성 <br>함수가 끝나면 소멸 | 
| 멤버 변수 | 클래스 멤버 변수 | 클래스 내부 private가 아닐 경우 다른 클래스 | heap | 인스턴스가 생성시 생성 <br>가비지 컬렉터가 메모리를 수거할 때 소멸 |
| static 변수 | static 예약어를 사용하여 클래스 내부 | 클래스 내부, private가 아닐 경우 클래스 이름으로 다른 클래스 | data | 프로그램이 처음으로 시작할 때 생성 <br> 프로그램이 끝나고 메모리를 해제할 때 소멸 | 
