## CS
## [Process, Thread, Context Switching 설명 및 차이](https://charlezz.medium.com/process%EC%99%80-thread-%EC%9D%B4%EC%95%BC%EA%B8%B0-5b96d0d43e37)
- Program : 어떤 작업을 하기 위해 실행할 수 있는 파일 또는 프로그램 
- Process : CPU로부터 자원을 할당받아 Program이 실행되고 있는 상태 
- Thread : 할당받은 자원을 이용하는 실행의 단위이고 프로세스 내에 여러개 생길 수 있다. 
  - 어플리케이션 하나가 Process이고, 그 안에서의 분기 처리가 Thread이다.
- Context Switching 시, Context Switching 을 수행하는 CPU는 Cache 를 초기화하고 Memory Mapping 을 초기화하는 작업을 거치는 등 아무 작업도 하지 못하므로 잦은 Context Switching은 성능 저하(오버헤드)를 가져온다.

