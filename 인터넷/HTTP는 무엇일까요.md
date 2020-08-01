# HTTP는 무엇일까요?

#### ❗ HTTP란?

HTTP(Hyper Text Transfer Protocol) 는 

텍스트 기반의 통신 규약이며 <u>"인터넷에서 정보를 주고 받을 수 있는 프로토콜"</u> 을 의미한다. 

80번 포트를 사용하며, [TCP](https://github.com/hjyeon-n/BE_TIL/blob/master/%EC%9D%B8%ED%84%B0%EB%84%B7/%EC%9D%B8%ED%84%B0%EB%84%B7%EC%9D%80%20%EC%96%B4%EB%96%BB%EA%B2%8C%20%EC%9E%91%EB%8F%99%EB%90%A0%EA%B9%8C%EC%9A%94.md) 와 [UDP](https://github.com/hjyeon-n/BE_TIL/blob/master/%EC%9D%B8%ED%84%B0%EB%84%B7/%EC%9D%B8%ED%84%B0%EB%84%B7%EC%9D%80%20%EC%96%B4%EB%96%BB%EA%B2%8C%20%EC%9E%91%EB%8F%99%EB%90%A0%EA%B9%8C%EC%9A%94.md)를 이용한다. 

HTTP는 웹에서만 사용하는 프로콜로 [TCP/IP](TCP/IP)를 기반으로 한 지점에서 다른 지점으로 요청과 응답을 전송한다.

<br/>

#### ❗ HTTP의 동작방식


![캡처](https://user-images.githubusercontent.com/64277114/89104649-cde70700-d455-11ea-90c3-8465e3408601.JPG)
<br/>
[^Client 이미지]: Icons made by <a href="http://www.freepik.com/" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon"> www.flaticon.com</a>

HTTP는 위의 그림처럼, client가 server에게 요청을 보내면 server가 응답하는 방식으로 동작한다.
<br/>

**✔** **요청 (Request)**

- 클라이언트가 서버에게 연락하는 것을 의미하며 요청을 보낼 때 요청에 대한 정보도 함께 보낸다.

  <br/>

**✔ 요청의 종류 (Request Method)**

- **GET**: URI형식으로 서버측 데이터를 요청한다.
- **POST**: 요청 URI에 폼 입력을 처리하기 위해 구성한 서버측 스크립트(ASP, PHP, JSP 등) 혹은 CGI 프로그램으로 구성되고, Form Action과 함께 전송된다. 이 때, 헤더 부분이 아닌 데이터 부분에 요청 정보가 포함된다.
- **HEAD**: GET 방식과 유사하나, 웹 서버에서 헤더 정보 이외에는 어떤 데이터도 보내지 않는다.
- **PUT**: POST 방식과 유사한 전송 구조를 가진다. 헤더 이외에 데이터가 함께 전송된다. 서버에 지정한 콘텐츠를 저장하기 위해 사용되며 홈페이지 변조에 많이 악용되고 있다.
- **DELETE**: 웹 서버에 파일을 삭제하기 위해 사용된다. (PUT과 반대개념)

<br/>

**✔ Request 메시지 예시**

GET https://github.com HTTP/1.1   ▶  메소드 구조 버전을 의미

User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...	▶  헤더 (요청에 대한 정보)

Upgrade-Insecure-Requests: 1   

▶ 본문은 헤더에서 한 줄을 띄고 구성되며 데이터를 담아 보내는 부분이다. 현재 예시에서는 ❌
<br/>


**✔ 응답 (Response)**

- 서버가 요청에 대한 답변을 클라이언트에 보내는 것이다.

<br/>

**✔ 응답 상태 코드 (Status Code)**

- **1XX (조건부 응답)**: 요청을 받았으며 작업을 계속한다.
- **2XX (성공)**: 클라이언트가 요청한 동작을 승낙해 성공적으로 처리했음을 의미한다.
- **3XX (리다이렉션 완료)**: 클라이언트가 요청을 마치기 위해 추가 동착을 취해야 함을 의미한다.
- **4XX (요청 오류)**: 클라이언트에 오류가 있음을 의미한다.
- **5XX (서버 오류)**: 서버가 요청 수행헤 실패했음을 의미한다.


<br/>
**✔ 응답 메시지 예시**

HTTP/1.1 200 OK   ▶  첫 줄은 버전, 상태 코드, 상태 메시지로 구성되어 있다.

Connection: keep-alive  ▶ 헤더 (응답에 대한 정보)

Content-Encoding: gzip

...

```null
<!DOCTYPE html><html lang="ko"><head><title...
```

▲ 본문 (HTML이 담겨 있으며 HTML을 통해 브라우저가 화면에 랜더링 한다. )

<br/>

#### ❗ HTTP의 특징

1. HTTP는 연결상태를 유지하지 않는 비연결성 프로콜이다.

   즉, 브라우저를 통해 사용자의 요청에 따라 서버와 접속해 요청에 대한 응답 데이터를 전송 후 연결을 종료한다. 이러한 점은 전산 자원이 적게 든다는 장점이 있지만, 사용자의 종료 후 추가적인 요청을 처리할 수 없다는 단점이 있다. 이를 해소하기 위해 Cookie, Session, URL Rewriting 등이 사용되고 있다.

2. HTTP 메시지는 HTTP 서버와 HTTP 클라이언트에 의해 해석된다.

3. HTTP는 요청을 독립적인 트랜잭션으로 취급한다.

   이전 요청과 다음 요청간에 관계가 없어 저장공간을 동적으로 할당할 필요가 없다. 따라서 클라이언트가 트랜잭션 도중 다운이 돼도 서버에서는 이를 처리할 필요가 없다. 하지만 이러한 점은 요청마다 추가 정보를 항상 해석해야 한다는 단점이 있다.

4. TCP/IP 의 socket을 이용해 연결되는 응용 계층 프로토콜이다.

<br/>

#### ❗ HTTP 1.1 VS HTTP 2.0

- 처리 방식
  * HTTP 1.1 은 앞의 요청에 대한 응답을 받아야만 다음 요청이 처리될 수 있었다. (HOL 블로킹 발생)
  * HTTP 2.0 에서는 Multiplexing 방식이 도입되어 동시에 여러 리소스를 받아올 수 있게 되었다.
- 데이터
  * HTTP 1.1 은 문자열 형식으로 전송되었다.
  * HTTP 2.0 은 binary로 인코딩하여 압축해 전송하며 요청 데이터간 의존관계 또한 지정할 수 있다.
- Server Push
  * HTML 문서상에 필요한 리소스를 클라이언트 요청없이 보낼 수 있는 HTTP 2.0에 추가된 기능이다.
