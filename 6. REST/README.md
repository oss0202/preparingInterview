### REST ( REpresentational State Transfer ) 
- 분산 하이퍼미디어 시스템(ex. Web)을 위한 아키텍쳐 스타일
- 아키텍쳐 스타일 : 제약조건들의 집합
  - client-server
  - stateless
  - cache
  - **uniform interface**
    - 아래 2가지를 잘 만족을 하지 못한다.
    - Self-descriptive message : 메세지 스스로 설명이 가능해야 한다.
    - HATEOAS : 링크를 통해 애플리케이션 상태 변화가 가능해야 한다.
  - layered system
  - code-on-demand(optional) : javascript
- 필요한 이유
  - 멀티 플랫폼(WEB 브라우저 이외의)에 대한 지원을 위해서 

### REST API
- API( Application Programming Interface)
  - 데이터와 기능의 집합을 제공하여 컴퓨터 프로그램간 상호작용을 촉진하며, 서로 정보를 교환 가능하도록 하는 것
- REST API
  - REST 기반으로 서비스 API를 구현한 것

### REST API 설계 규칙
- URI은 정보의 자원을 표현해야 한다.
- 자원에 대한 행위는 HTTP Method(GET, PUT, POST, DELETE, PATCH)로 표현한다.
- 슬래시 구분자(/)는 계층 관계를 나타내는데 사용한다.
- URI 마지막 문자로 슬래쉬(/)를 포함하지 않는다.
- 하이픈(-)은 URI 가독성을 높이는데 사용한다.
- 밑줄(_)은 가독성을 위해 URI에 사용하지 않는다.
- URI는 대소문자를 구별하므로 소문자가 적합하다.
- 파일확장자는 URI에 포함하지 않는다.
- 리소스 간에 연관관계가 있는 경우
  - /리소스명/리소스ID/관계가 있는 다른 리소스명
  - ex. /users/{userid}/devices : 일반적으로 소유관계 표현할 때

#### ※ 응답코드
- 1xx : 전송 프로토콜 수준의 정보 교환
- 2xx : 클라이언트 요청이 성공적으로 수행됨
- 3xx : 클라이언트는 요청을 완료하기 위해 추가적인 행동을 취해야함
- 4xx : 클라이언트의 잘못된 요청
- 5xx : 서버쪽 오류로 인한 상태코드

### RESTful
- REST 아키텍처를 구현하는 웹서비스를 나타내는 용어이다.
- RESTful API의 목적은 성능 향상에 있는 것이 아니라 일관적인 컨벤션을 통한 API의 이해도 및 호환성을 높이는 것이다.