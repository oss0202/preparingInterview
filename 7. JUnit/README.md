## JUnit
### JUnit을 왜 사용하는가?
- 코드의 신뢰성을 높히고 빠르고 쉽게 구현
- 변경에 대한 과거 비즈니스로직 대한 검증

### 단위테스크 코드 5원칙( FIRST )
1. F - Fast : 테스트코드는 빠르게 실행되어야 한다.
2. I - Independent : 독립적으로 실행되어야 한다.
3. R - Repeatable : 반복 실행 가능해야 한다.
4. S - Self Validating : 메뉴얼 없이 테스트 코드만 성공해도 성공, 실패여부를 파악할 수 있어야 한다.
5. T - Timely : 즉시 사용 가능해야 한다.

### JUnit4, 5 실행 순서
- @Before(4), @BeforeEach(5) : 테스트 클래시의 각 테스트 메서드 실행 전 실행
- @After(4), @AfterEach(5) : 테스트 클래시의 각 테스트 메서드 실행 후 실행
- @BeforeClass(4), @BeforeAll(5) : 테스트 클래스의 모든 테스트 메서드가 실행 전에 실행
- @AfterClass(4), @AfterAll(5) : 테스트 클래스의 모든 테스트 메서드가 실행 후 실행
- @Test(4,5) : 클래스의 테스트 케이스
  <br>![junit](../img/junit.img) 

### @Runwith 어노테이션
JUnit 프레임워크 테스트 실행방법을 확장할 때 사용하는 어노테이션이다.
<br>ex. @Runwith(SpringRunner.class)는 스프링 부트와 JUnit 사이의 연결자 역할

### @WebMvcTest 어노테이션
스프링 부트의 컨트롤러를 JUnit으로 테스트하고 싶을 경우 Http Connection을 별도로 구현하지 않아도 MVC 테스트를 가능하게 할 수 있다.
- @WebMvcTest 자체의 기능은 컨트롤러가 예상대로 동작하는지 테스트하는 것이다. 다만, @Controller, @ControllerAdvise, @JsonComponent, Converter, GenericConverter, Filter, HandlerInterceptor, WebMvcConfigurer, HandlerMethodArgumentResolver 이 붙은 클래스만 스캔하도록 제한한다.

### MockMvc 객체란
- MockMvc는 웹 애플리케이션의 구동 없이 스프링 MVC의 동작을 재현할 수 있다.

1. perform()
   - DispatcherServlet에 요청
   - MockMvcRequestBuilder클래스를 사용해 설정한 요청 데이터를 perform()의 인수로 전달한다.
   - get, post, put, delete와 같은 메서드를 제공한다.
   - ResultActions 인터페이스를 반환한다.
2. 요청 데이터 설정
   - perform 메소드로 테스트 할 url을 설정했다면 이 url이 요청할 데이터 또한 설정할 수 있다.
   - MockHttpServletRequestBuilder 클래스가 이 기능을 제공한다.
   - **MockHttpServletRequestBuilder 주요 메서드**
     - param / params
       - 요청 파라미터 설정
     - header / headers
       - 요청 헤더 설정
       - contentTYpe & accept와 같은 특정 헤더를 설정하는 메서드도 제공
     - cookie
       - 쿠키 설정
     - content
       - 요청 본문 설정
     - requestAttr
       - 요청 스코프에 객체를 설정
     - flasgAttr
       - 플래시 스코프에 객체를 설정
     - sessionAttr
       - 세션 스코프에 객체를 설정
3. ResultActions 인터페이스
   - andDo()
     - log() : 실행결과를 디버깅 레벨에서 로그로 출력
     - print() : 실행결과를 임의의 출력대상에 출력, 출력대상을 지정하지 않으면 System.out 으로 출력한다.
   - andExpect()
     - 인수에 실행결과를 검증하는 MockMvcResultMatchers에서 제공하는 ResultMatcher을 지정한다.
     - **MockMvcResultMatcher 주요 메서드**
       - status
         - HTTP 상태 코드 검증
       - header
         - 응답 헤더의 상태 검증
       - cookie
         - 쿠키 상태 검증
       - content
         - 응답 본문 내용 검증 jsonPath나 xpath와 같은 특정 콘텐츠를 위한 메서드도 제공
       - view
         - 컨트롤러가 반환한 뷰 이름 검증
       - forwardedUrl
         - 이동대상의 경로를 검증, 패턴으로 검증할때는 forwardedUrlPattern 메서드를 사용
       - redirectedUrl
         - 리다이렉트 대상의 경로 또는 URL 검증 패턴으로 검증할때는 redirectedUrlPattern 메서드를 사용
       - model
         - 스프링 MVC 모델 상태 검증
       - flash
         - 플래시 스코프의 상태 검증
       - request
         - 서블릿 3.0부터 지원되는 비동기 처리의 상태나 요청 스코프의 상태, 세션 스코프의 상태 검증
   - andReturn()
     - return 결과를 반황할 때 쓰인다.

4. Given - When- Then 패턴(  준비 - 실행 - 검증 )
- 대표적인 테스트 방식으로 행위주도개발(Behavior-Driven-Development BDD)방식의 접근법
- Given
  - 테스트를 위해 준비를 하는 과정
  - 테스트에 사용되는 변수, 입력 값 등을 정의하거나 Mock 객체를 정의하는 구문도 Given에 포함
- When
  - 실제로 액션을 하는 테스트를 실행하는 과정
- Then
  - 테스트를 검증하는 과정
  - 주로 assertThat 메서드로 When에서 얻어낸 값과 비교한다.

5. AssertJ
- 단언문(assertion)을 작성하기 위한 인터페이스를 제공하는 자바 라이브러리
- 테스트 코드의 가독성을 향상시키고 테스트 유지관리를 더 쉽게 만드는 것이 목적
- spring-boot-starter-test에 기본적으로 포함
- 장점
  - 메서드 체이닝을 지원하여 깔끔하고 읽기 쉬운 테스트 코드 작성 가능
  - ※ junit의 assertThat은 ide에서 자동완성을 잘 지원안한다. 
- 단점
  - 라이브러리 의존성 설정
    - java 8 이상은 3.x 버전
    - java 7 이하는 2.x 버전




