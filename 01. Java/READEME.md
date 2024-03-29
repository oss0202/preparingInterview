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
![java_generic](../img/java_generic.png)

### Java Reflection 이란?
- JVM에서 실행되는 애플리케이션의 런타임 동작을 검사하거나 수정하는 기능이 필요한 프로그램에서 사용됩니다.
- 클래스의 타입을 알지 못해도 그 클래스의 메서드, 타입, 변수 등을 접근할 수 있도록 해주는 API입니다.
- 대표적으로 ORM기술인 하이버네이트, jackson라이브러리 등에 사용됩니다.

### Java Optional 이란?
- Java8 이후로 사용 가능하다.
- "존재할 수도 있지만 안 할 수도 있는 객체", 즉 "null이 될 수도 있는 객체"를 감싸고 있는 일종의 래퍼 클래스이다.
- **효과**
  - NPE(NullPointException)을 유발할 수 있는 null을 직접 다루지 않아도 된다.
  - null 체크를 직접 하지 않아도 된다.
  - 명시적으로 해당 변수가 null일 수도 있다는 가능성을 표현할 수 있다.(따라서 불필요한 방어 로직을 줄일 수 있다.)


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

### Comparable vs Comparator 차이
- 목적 : 객체를 비교할 수 있도록 만든다.
    - primitive type의 실수 변수(int, double 등)의 경우 부등호를 통해서 비교할 수 있다.
- 둘 다 인터페이스이다.
  - 인터페이스 내에 있는 메소드를 반드시 구현해야 한다.
- **비교 대상이 다르다.**
1) Comparable
   - **compareTo(T o)**
   - 자기 자신과 매개변수 객체를 비교
2) Comparator
   - **compare(T o1, T o2)**
   - 두 매개변수 객체를 비교

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

## Abstract Class(추상클래스) vs Interface(인터페이스)
### 공통점
- 선언부만 있고 구현이 없는 클래스이다.
- 자기 자신이 직접 객체를 생성할 수 없으며, 자식 클래스가 추상클래스를 상속(extend)받거나, 인터페이스를 구현(implements)하여 객체를 생성할 수 있다.
- 선선된 type과 자식의 type이 같아야만 한다.

### 차이점
1. Abstract Class(추상클래스)
- ~~추상메소드를 하나라도 가지고 있는 클래스~~
- 추상메소드가 없어도 괜찮다.
- 조건
  - non-static, non-final 필드 및 public, protected, private 메소드를 사용할 수 있다.
  - 추상클래스를 상속받은 클래스는 반드시 추상 메소드를 구현해야 한다.
  - **다중 상속이 불가능하다.**
- **목적**
  - **공통적인 기능을 하는 객체들의 추상화**
  - is - a 관계( ~ 이다.)
    - 만들어야 할 여러 클래스들의 공통점을 찾아 추상화시켜서 사용하는 것

2. Interface(인터페이스)
- 상수(final, static final), 추상메소드만 가지고 있는 클래스
- 조건
  - 인터페이스를 구현하는 클래스는, 인터페이스의 모든 메소드를 구현해야한다.
  - **다중 상속이 가능하다.**
- **목적**
  - 구현 객체가 같은 동작을 한다는 것을 보장하기 위해서
    - has - a 관계( ~ 을 할 수 있는)
      - 구현하는 모든 클래스에 대해 특정 메소드가 반드시 존재하도록 강제하는 역할

### 정리
추상클래스만으로도 충분히 인터페이스의 역할을 대신할 수 있다. 그런데 왜 굳이 2가지로 나눠서 사용할까? 이론상
추상클래스만으로 인터페이스 역할을 대신할 순 있지만 실제로 개발을 하다보면 둘의 사용용도는 다르다는 걸 알 수 있다.

- 사용용도의 차이점
  - 추상클래스는 **IS-A "~이다.**"
  - 인터페이스는 **HAS-A "~을 할 수 있는**"

자바의 특성상 한 개의 클래스만 상속이 가능하기 때문에 해당 클래스의 구분을 추상클래스 상속을 통해 해결하고, 해당 클래스가 할 수 있는 기능들에 대해서는 여러 개의 상속(구현)이 가능한 인터페이스로 구현한다.

추상클래스를 사용하지 않고 인터페이스로만 기능을 구현할 경우 인터페이스 내의 정의한 모든 메서드들을 다시 오버라이딩 해야하는 번거로움이 있다. 불필요한 메서드까지 오버라이딩 해야 한다.

반대로 추상클래스로만 클래스의 기능을 구현할 경우 자바는 하나의 클래스만 상속할 수 있기 때문에 추상클래스에 모든 메서드가 들어있어야 한다. 

따라서 추상클래스와 인터페이스를 적절히 섞어 개발을 해야한다.

- 추상클래스 사용 시기
  - 상속관계를 쭉 타고 올라갔을 때, **같은 조상 클래스를 상속**하는 데 **기능까지 완벽히 똑같은 기능이 필요한** 경우
- 인터페이스 사용 시기
  - 상속관계를 쭉 타고 올라갔을 때, **다른 조상 클래스를 상속**하는 데 **같은 기능이 필요**한 경우

## Annotation(@, 어노테이션)
자바 소스 코드에 추가하여 사용할 수 있는 메타데이터의 일종이다. 보통 @ 기호를 앞에 붙여서 사용한다.
JDK 1.5 버전 이상에서 사용 가능하다. 자바 어노테이션은 클래스 파일에 임베디드되어 컴파일러에 의해 생성된 후 자바 가상머신에 포함되어 작동한다.

### 어노테이션의 기능
- 컴파일러에게 코드 작성 문법 에러를 체크하도록 정보 제공
- 소포트웨어 개발 환경이


### 어노테이션의 종류
- **표준(내장) 어노테이션** : 자바가 기본적으로 제공해주는 어노테이션
- **메타 어노테이션** : 어노테이션을 위한 어노테이션
- **커스텀 어노테이션** : 사용자가 직접 정의하는 어노테이션

### 1. 표준 어노테이션
1. @Override
   - 오버라이딩을 올바르게 했는지 컴파일러가 체크한다.
2. @Deprecated
   - 앞으로 사용하지 않을 것을 권장하는 필드나 메서드에 붙인다.
   - 자바는 하위 호환성을 엄청나게 중요하게 여기기 때문에 유지는 하되, 권장하지 않는다.
3. @SuppressWarnings
    - 컴파일러의 경고메세지가 나타나지 않게 한다.
    - 보통 경고가 많을 때, 확인된 경고는 해당 어노테이션을 붙여서 새로운 경고를 알아보지 못하는 것을 방지하기 위해 사용한다.

### 2. 메타 어노테이션
커스텀 어노테이션을 만들 때 사용하는 메타 어노테이션들도 있다. 메타 어노테이션에 대해서 잘 알고 있어야 정확히 원하는 커스텀 어노테이션을 만들어 사용할 수 있다.

1. @Retention
    - 어노테이션의 리텐션 기간을 명명한다.
    - **RetentionPolicy.Class**
      - 바이트 코드 파일까지 어노테이션 정보를 유지한다.
      - 리플렉션을 이용해서 어노테이션 정보를 얻을 수는 없다.
    - **RetentionPolicy.Runtime**
      - 바이트 코드 파일까지 어노테이션 정보를 유지하면서 리플렉션을 이용해 런타임에 어노테이션 정보를 가져올 수 있다.
    - **RetentionPolicy.Source**
      - Compile 이후에는 삭제된다.
2. @Documented
   - 자바 문서에도 어노테이션 정보가 표현된다.
3. @Target
    - 생성할 어노테이션이 적용될 수 있는 위치를 나열한다.
    - **ElementType.Type**
      - 클래스, 인터페이스, 열거 타입
    - **ElementType.ANNOTATION_TYPE**
      - 어노테이션
    - **ElementType.FILED**
      - 필드
    - **ElementType.CONSTRUCTOR**
      - 생성자
    - **ElementType.METHOD**
      - 메소드
    - **ElementType.LOCAL_VARIABLE**
      - 로컬변수
    - **ElementType.PACKAGE**
      - 패키지
4. @Inherited
   - 자식 클래스가 어노테이션을 상속 받을 수 있다.
5. @Repeatable
    - 반복적으로 어노테이션을 선언할 수 있다.

## 자바 동기화 처리( **volatile** vs **synchronized**)
### volatile
CPU메모리 영역에 캐싱된 값이 아니라 항상 최신의 값을 가지도록 메인 메모리 영역에서 값을 참조하도록 할 수 있다.
volatile를 사용한다고 해서 모든 동기화 문제가 해결되는 것은 아니다. 단지 캐시없이 최신의 값을 보게 할 뿐이다.
```text
1) 변수 a =1
2) 1번 스레드가 a에 값을 증가시키기 위해 a의 값을 읽습니다. a=1
3) 1번 스레드가 1 + 1을 계산하여 2를 얻습니다. (아직 저장은 안 함)
4) 2번 스레드가 a에 값을 증가시키기 위해 a의 값을 읽습니다. a=1 
5) 1번 스레드가 변수 a에 2를 저장
6) 2번 스레드가 1 + 1을 계산하여 2를 얻습니다. (아직 저장은 안 함)
7) 2번 스레드가가 변수 a에 2를 저장
```
의도대로라면 1, 2번 스레드에서 각각 1을 더하기 때문에 3이 되어야 하겠지만 위 순서대로 처리되면서 a의 최종값은 2가 된다.

### synchronized

https://jronin.tistory.com/110


## Java short-circuit
###쇼트 서킷이란
논리연산자 AND, OR 을 나타내기 위해 부호 &&, || 을 사용하는 것을 의미한다.
- &&, || 와 &, | 를 비교할 때, 둘은 최종적으로 같은 결과를 내지만 다른 과정을 거친다.
  - &, | : 연산자의 앞 조건식과 뒤 조건식을 **둘 다** 실행 시킨다.
  - &&, || : 연산자의 앞 조건식의 결과에 따라 뒤 조건식의 실행 여부를 결정한다.
    - 이러한 논리연산자를 특별히 "쇼트 서킷"이라 한다.
- 쇼트 서킷에서는 && 앞의 boolean 값이 **false** 일 때, **&& 뒤를 굳이 실행하지 않음**으로 불필요한 연산을 생략한다.
- 쇼트 서킷에서는 || 앞의 boolean 값이 false 일 때만 뒤를 실행한다.(|| 앞쪽이 True 라면 굳이 뒤를 연산하지 않는다.)
