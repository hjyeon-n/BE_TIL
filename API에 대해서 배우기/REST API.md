# REST API 🛒

### ❓ REST란?

Representational State Transfer의 약자

월드 와이드 웹과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 개발 아키텍처의 형식

웹에 존재하는 모든 자원(이미지, 동영상, DB 자원)에 고유한 URI를 부여해 활용하는 것

이런 REST의 형식을 따른 시스템을 RESTful 이라고 부름

<br/>

**✔ REST의 CRUD Operation**

* Create: 생성 (POST)
* Read: 조회 (GET)
* Update: 수정 (PUT)
* Delete:  삭제 (DELETE)

<br/>

### ❗ REST 구성요소

1. 자원 (Resource): URI
   * 모든 자원에 고유한 ID가 존재하며 서버에 보관됨
   * Client는 URI를 이용해 자원을 저장하고 해당 자원의 정보에 대한 조작을 Server에 요청
2. 행위 (Verb): HTTP Method
   * HTTP 프로토콜의 GET, POST, PUT, DELTE 와 같은 메소드를 사용
3. 표현 (Representation of Resource)
   * REST에서 하나의 자원은 JSON, XML, TEXT, RSS등 여러 형태의 Representation으로 나타냄

<br/>

### ❗ REST의 특징

1. Server-Client (서버-클라이언트 구조)

   * 자원이 있는 쪽이 Server, 자원을 요청하는 쪽이 Client

2. Stateless (무상태)

   * 클라이언트의 context를 서버에 저장하지 않음

   * 세션과 쿠키와 같은 context 정보를 신경쓰지 않아도 되므로 구현이 단순해짐

3. Cacheable (캐시 처리 가능)

   * HTTP 프로토콜을 사용하므로, 웹에서 사용하는 기존의 인프라를 그대로 활용

4. Layered System (계층화)

   * API 서버는 순수 비즈니스 로직 수행, 그 앞단은 사용자 인증과 같은 계층을 추가해 구조상의 유연성을 줄임

5. Uniform Interface (인터페이스 일관성)

   * URI로 지정한 자원에 대한 조작을 통일되고 한정적인 인터페이스로 수행
   * HTTP 표준만 따르면 모든 플랫폼에서 사용 가능

<br/>

### ❗ REST의 장·단점

😉 장점

* HTTP 프로토콜의 인프라를 그대로 사용하므로 REST 사용을 위한 별도의 인프라 구축 필요 없음
* HTTP 표존 프로토콜을 따르는 모든 플랫폼에서 사용 가능
* Hypermedia API의 기본을 충실히 지키면서 범용성을 보장
* 서버와 클라이언트의 역할을 명확히 분리

😣 단점

* 표준이 존재하지 않음
* HTTP Method 형태가 제한적임
* 구형 브라우저에서는 PUT이나 DELETE 등을 사용하지 못함

<br/>

### ❗ URI 설계 시 주의할 점

1. 슬래시(/)는 계층 관계를 나타내는 데 사용

   ex) http://petMateistheBest.com/animals/dogs

2. URI 마지막 문자로 슬래시를 포함하지 않아야 함

   ex) http://petMateistheBest.com/animals/dogs/ (❌)

3. 하이픈(-)은 URI 가독성을 높이는 데 사용

4. 밑줄(_)은 URI에 사용하지 않아야 함

5. URI 경로에는 소문자가 적합함

6. 파일 확장자는 URI에 포함시키지 않아야 함

   ex)  http://petMateistheBest.com/animals/dogs/kong.jpeg (❌)