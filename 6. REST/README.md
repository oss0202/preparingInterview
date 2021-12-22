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
- HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)를 명시하고, 
HTTP Method(POST,GET, PUT, DELETE)를 통해
해당 자원에 대한 CRUD Operation을 적용하는 것을 의미한다.
- 필요한 이유
  - 멀티 플랫폼(WEB 브라우저 이외의)에 대한 지원을 위해서 

### REST API


### RESTful