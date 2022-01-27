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
  - NPE 방지
- Field 주입(@Autowired)
  - 편하다.
  - DI프레임워크(Spring)에 의존적이다.
- Setter 주입
  - 주입받는 객체가 변경될 가능성이 있다.

### Spring MVC 기본 동작 흐름
![spring_mvc_exec_ord](../img/spring_mvc_exec_ord.img)

|구성요소 이름|설명|
|:---:|:---|
|Dispatcher Servlet| - 클라이언트의 요청을 받아 컨트롤러에게 전달, 컨트롤러가 리턴한 결과값을 View에 전달하여 알맞은 응답생성<br>- HTTP 프로토콜로 들어오는 모든 요청을 가장 먼저 받아 적합한 컨트롤러에 위임해주는 프론트 컨트롤러(Front Controller)이다.
|Handler Mapping| 클라이언트의 요청 URL을 어떤 컨트롤러가 처리할지 결정
|Handler Adapter| Dispatcher Servlet 처리 요청을 변환해서 컨트롤러에게 전달, 그 응답결과를 Dispatcher Servlet이 요구하는 형식으로 변환
|Controller| 클라이언트의 요청을 처리한 뒤, 결과를 리턴
|Model And View| 컨트롤러가 처리한 결과 정보 및 뷰 선택에 필요한 정보를 담음
|View Resolver| 컨트롤러의 처리 결과를 보여줄 뷰를 결정
|View| 컨트롤러의 처리 결과 화면을 생성, JSP 템플릿 파일등을 이용
* Database를 제외한 파란색 부분은 모두 Spring MVC가 제공
* 보라색 부분은 개발자가 구현해야하며, 녹색 부분인 View는 Spring이 제공하는 부분도 있고, 개발자가 구현해야하는 부분도 있다.

#### 요청 흐름 ####
1. **클라이언트의 모든 요청을 Dispatcher Servlet이라는 Servlet Class가 받는다.**
2. **Dispatcher Servlet(Front Contoller)은 요청 URL을 Handler Mapping에게 전달하고, 현재 요청에 알맞는 Contoller와 Method에 대한 정보를 알아낸다.**
   - 어떤 요청에 어떤 Contoller가 동작할지를 xml파일이나 Java파일의 어노테이션으로 설정
   - Spring으로 만들어진 Web Application이 실행될 때, Handler Mapping 객체들이 생성되면서 이런 정보들을 관리함
3. **Dispatcher Servlet은 HandlerAdapter에게 요청 처리를 위임한다.**
4. **Handler Adapter는 Controller와 해당 메서드를 실행한다.**
   - HandlerMapping은 DispatcherServlet으로 부터 전달된 URL을 바탕으로 HandlerAdapter 객체를 포함하는 HandlerExecutionChain 객체를
생성하며, 이후 DispatcherServlet이 HandlerExecutionChain 객체로부터 HandlerAdapter 객체를 가져와서 해당 메소드를 싱행하게 된다.
5. **Controller는 비즈니스 로직을 처리하고, 그 결과를 바탕으로 뷰(ex. JSP)에 전달할 객체를 Model 객체에 저장한다.**
   - Dispatcher Servlet에게 View name을 리턴
   - Model : Controller에서 View로 넘겨줄 객체가 저장되는 곳
6. **Dispatcher Servlet은 view name을 View Resolver에게 전달하여 View 객체를 얻는다.**
   - accept와 같은 header 정보도 같이 전달
   - header 정보 내의 Accept는 HTML, JSON, XML 일 수 있고, 기본적으로는 HTML
   - View Resolver는 전달된 정보를 바탕으로 사용자에게 보여줄 View가 무엇인지 결정
   - JSP인 경우 JstlView 객체가 생성되며, JstlView 객체가 "xxxx.jsp"에 포워딩하여 결과를 보여준다.(JSP 객체를 생성하는 것의 아니다.)
7. **Dispatcher Servlet은 View 객체에 화면 표시를 요청한다.**
8. **View 객체는 해당하는 뷰(ex. JSP, Thymeleaf)를 호출하며, 뷰는 Model 객체에서 화면 표시에 필요한 객체를 가져와 화면 표시를 처리한다.**
  
### Spring, Spring Boot 차이점
- Spring Boot는 embedded Tomcat을 사용하기 때문에 따로 Tomcat을 설치하거나 매번 버전을 관리안해도 된다.
- stater를 통한 dependency 자동화
  - 과거 Spring framework에서는 각각의 dependency들의 호환되는 버전을 일일이 맞추어야 했지만 starter가 대부분의 dependecny를 관리해주기 때문에 편해졌다.
- XML 설정을 하지 않아도 된다.

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

### 대표적인 스프링 디자인패턴
- Adapter Pattern
  - 대표적으로 JDBC가 어뎁터 패턴을 이용해서 다양한 데이터베이스 시스템을 단일한 인터페이스로 조작할 수 있게 해준다.
  - OCP와 DIP가 활용된 설계 패턴이다.
- Proxy Pattern
- Decorator Pattern
- Singleton Pattern
- Template Method Pattern
- Factory Method Pattern
- Strategy Pattern
- Template callback Pattern

## Filter, Interceptor
### 필터(Filter)
J2EE 표준 스펙기능으로 디스패처 서블릿(Dispatcher Servlet)에 요청이 전달되기 전/후에 url패턴에 맞는 모든 요청에 대해 부가작업을 처리할 수 있는 기능을 제공
![spring_filter](../img/spring_filter.img)
**필터 메소드**
- **init 메소드**
  - 필터 객체를 초기화하고 서비스에 추가하기 위한 메소드
  - 웹 컨테이너가 1회 init 메소드를 호출하여 필터 객체를 초기화하면 이후의 요청들은 doFilter를 통해 처리된다.
- **doFilter 메소드**
  - url-pattern에 맞는 모든 HTTP 요청이 디스패처 서블릿으로 전달되기 전에 웹 컨테이너에 의해 실행되는 메소드
- **destroy 메소드**
  - 필터 객체를 서비스에서 제거하고 사용하는 자원을 반환하기 위한 메소드
  - 웹 컨테이너에 의해 1번 호출되며 이후에는 doFilter에 의해 처리되지 않는다.


### 인터셉터(Interceptor)
Spring이 제공하는 기술로써, 디스패처 서블릿(Dispatcher Servlet)이 컨트롤러를 호출하기 전과 후에 요청과 응답을 참조하거나 가공할 수 있는 기능을 제공
- **웹컨테이너에서 동작하는 필터와 달리 인터셉터는 스프링 컨텍스트에서 동작한다.**
![spring_Interceptor](../img/spring_Interceptor.img)

**인터셉터 메소드**
- **preHandle 메소드**
  - 컨트롤러가 호출되기 전에 실행, 컨트롤러 이전에 처리해야 하는 전처리 작업이나 요청정보를 가공하거나 추가하는 경우에 사용
  - 반환 타입은 boolean인데 true일 경우에만 다음단계로 진행
- postHandle 메소드
  - 컨트롤러가 호출된 후에 실행, 컨트롤러 이후에 처리해야하는 후처리 작업이 있을 때 사용
  - 컨트롤러가 반환하는 ModelAndView 타입의 정보가 제공되는게, 최근에는 Json형태로 데이터를 제공하는 RestAPI 기반의 컨트롤러(@RestController)를 만들면서 자주 사용되지 않음
- afterCompletion 메소드
  - 모든 뷰에서 최종 결과를 생성하는 일을 포함해 모든 작업이 완료된 후에 실행
  - 요청 처리 중에 사용한 리소스를 반환할 때 사용하기에 적합

## 인터셉터(Interceptor)와 AOP(Aspect Oriented Programmin, 관점지향 프로그래밍) 비교
인터셉터 대신에 컨트롤러들에 적용할 부가기능을 어드바이스로 만들어 AOP를 적용할 수도 있다. 하지만 
다음과 같은 이유들로 컨트롤러의 호출 과정에 적용되는 부가기능들은 인터셉터를 사용하는 편이 낫다.
- Spring 컨트롤러는 타입과 실행 메소드가 모두 제각각이라 포인트컷(적용할 메소드 선별)의 작성이 어렵다.
- Spring 컨트롤러는 파라미터나 리턴값이 일정하지 않다.

## 필터 vs 인터셉터
|대상|필터(Filter)|인터셉터(Interceptor)|
|:------:|:---|:---|
|관리되는 컨테이너 | 웹 컨테이너 | 스프링 컨테이너|
|Request/Response<br>조작 가능 여부| O | X |
|실행시점 | DispatcherServlet 이전, 이후 | DispatcherServlet이 컨트롤러 호출하기 전, 후|
|용도|- 보안 관련 공통작업<br>- 모든 요청에 대한 로깅 또는 감사<br>- 이미지/데이터 압축 및 문자열 인코딩|- 인증/인가 등과 같은 공통 작업<br>- Controller로 넘겨주는 정보의 가공<br>- API 호출에 대한 로깅 또는 감사|
