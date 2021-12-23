### JUnit을 왜 사용하는가?
- 코드의 신뢰성을 높히고 빠르고 쉽게 구현
- 변경에 대한 과거 비즈니스로직 대한 검증

### JUnit4, 5 실행 순서
- @Before(4), @BeforeEach(5) : 테스트 클래시의 각 테스트 메서드 실행 전 실행
- @After(4), @AfterEach(5) : 테스트 클래시의 각 테스트 메서드 실행 후 실행
- @BeforeClass(4), @BeforeAll(5) : 테스트 클래스의 모든 테스트 메서드가 실행 전에 실행
- @AfterClass(4), @AfterAll(5) : 테스트 클래스의 모든 테스트 메서드가 실행 후 실행
- @Test(4,5) : 클래스의 테스트 케이스
  <br>![junit](../img/junit.img) 