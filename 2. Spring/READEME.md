### Spring Framework란?
- Java 플랫폼에서 엔터프라이즈급 애플리케이션을 개발하기 위한 오픈소스 애플리케이션 프레임워크 

### 프레임워크와 라이브러리의 차이는?
- 프레임워크
  - 프로그램의 전체적인 흐름을 자체적으로 가지고 있다
  - 프레임워크가 사용자가 작성한 코드를 호출해서 사용한다.(ex. Spring, JUnit)
- 라이브러리
  - 사용자가 프로그램의 전체적인 흐름을 제어한다.
  - 사용자가 코드로써 라이브러리의 특정 기능을 가져다 쓴다.

### IoC, DI란?
- IoC(Inversion of Control)
  - 프로그램의 제어권이 프레임워크로 넘어가서 Spring Framework에서 개발자의 코드를 호출하는 것
  - DL(Dependency Lookup)과 DI(Dependency Injection)에 의해서 구현된다.
    - DL : 클래스 및 계층간에 필요한 의존관계를 빈 설정 정보를 바탕으로 IoC Container가 의존성을 찾아주는 것
    - DI : 의존성을 주입해 주는 것

### AOP란?
- Aspect Oriented Programming
- 여러 모듈에서 공통적으로 사용하는 기능 및 로직들을 모듈화하는 프로그래밍 패러다임

### PSA란?
- Portable Service Abstraction
- 환경과 세부 기술의 변화에 관계없이 일관된 방식으로 기술에 접근할 수 있게 해주는 것(JDBC, JPA, Transaction Manager, ...)

### IoC Container란?
- Spring Bean, 객체의 생성, 관계설정, 사용, 제거 등의 전체 Lifecycle을 관리해 주는 컨테이너

### IoC Container에 Bean을 등록하는 방법
- xml 설정파일
- Configuration annotation사용

### IoC Container로부터 Bean을 주입받는 방법
- 생성자 주입
  - 객체의 불변성 확보
  - final로 선언 가능하다.
  - 순환참조를 방지한다.
- Field 주입(@Autowired)
  - 편하다.
  - DI프레임워크(Spring)에 의존적이다.
- Setter 주입
  - 주입받는 객체가 변경될 가능성이 있다.
  
### Spring, Spring Boot 차이점
- Spring Boot는 embedded Tomcat을 사용하기 때문에 따로 Tomcat을 설치하거나 매번 버전을 관리안해도 된다.
- stater를 통한 dependency 자동화
  - 과거 Spring framework에서는 각각의 dependency들의 호환되는 버전을 일일이 맞추어야 했지만 starter가 대부분의 dependecny를 관리해주기 때문에 편해졌다.
- XML 설정을 하지 않아도 된다.

### Filter, Interceptor
  |대상|필터(Filter)|인터셉터(Interceptor|
  |:------:|:---|:---|
  |실행시점 | DispatcherServlet 이전, 이후 | DispatcherServlet이 컨트롤러 호출하기 전, 후|
  |용도|- 보안 관련 공통작업<br>- 모든 요청에 대한 로깅 또는 감사|- 인증/인가 등과 같은 공통 작업<br>- Controller로 넘겨주는 정보의 가공|

### ORM ( Object-relational mapping ) - JPA( Java Persistent API )
- 객체와 관계형 데이터베이스의 데이터를 자동으로 연결해주는 개념이다.
- 객체 간의 관계를 바탕으로 SQL을 자동으로 생성해준다.
- 장점
  - 프로그래머가 로직에 더 집중할 수있다.
  - 가독성 및 유지보수의 편리성 증가
  - DBMS에 종속적이지 않다. 
- 단점
  - ORM으로만 서비스를 구현하기 어렵다.
  - 프로시저가 많을 경우 ORM을 활용하기 어렵다.

### SQL Mapper - Mybatis
- java와 SQL사이의 자동 매핑을 지원한다.
- 장점
  - 복잡한 쿼리 작성 가능
- 단점
  - 비슷한 쿼리 남발


