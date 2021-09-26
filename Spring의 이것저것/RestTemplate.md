# RestTemplate

예전에 학교에서 배웠던 것 같은데 기억이 잘 나지 않아서 새로 정리해둔다! 😉

<br>

### RestTemplate이 뭐지? 🙄

Spring에서 제공하는 간편하게 RestAPI를 호출할 수 있는 템플릿이며 http 통신에 유용하게 쓰일 수 있다. 반복적이고 기계적인 코드를 깔끔하게 줄여주고, json과 xml 응답을 쉽게 받을 수 있다는 특징이 있다. RestTemplate 클래스는 REST 서비스를 호출하도록 설계되어 HTTP 프로토콜의 메서드 (ex. GET, POST, DELETE, PUT)에 맞게 여러 메서드를 제공한다.

<br>

### HTTP 서버와 다양한 통신방법

+ URLConnection

  : URL의 내용을 읽어오거나 URL 주소에 GET, POST로 데이터를 전달할 때 사용한다.

  + new URL("http:// ....")
  + openConnection()
  + URLConnection
  + getInputStream, getOutputStream
  + InputStream, OutputStream 처리
  + 문제점
    + 응답코드가 4xx 거나 5xx 면 IOException 발생
    + 타임아웃 설정 불가
    + 쿠키 제어 불가

  <br>

+ HttpClient

  + CloseableHttpClient httpclient = HttpClients.createDefault();
  + 메소드에 따라 new HttpGet("http:// ....");
  + CloseableHttpResponse response = httpclient.execute(httpget);
  + HttpEntity entity = response.getEntity();
  + Stream으로 entity.getContent() 처리 등
  + URLConnection 와 비교하였을 때 장점
    - 모든 응답코드를 읽을 수 있다. 
    - 타임아웃 설정 가능
    - 쿠키 제어 가능
  + 문제점
    + URLConnection 을 이용한 방식보다 코드가 간결해졌지만, 여전히 반복적이고 코드들이 길다.
    + 스트림 처리 로직을 별도로 작성해야 한다.
    + 응답의 컨텐츠 타입에 따라 별도 로직이 필요

<br>

### RestTemplate의 동작원리

HttpClient는 HTTP를 사용하여 통신하는 범용 라이브러리이고, RestTemplate은 HttpClient 를 추상화(HttpEntity의 json, xml 등)해서 제공한다. 따라서 내부 통신(HTTP connection)에 있어서는 Apache HttpComponents 를 사용한다. 만약 RestTemplate 가 없다면, 직접 json, xml 라이브러리를 사용해서 변환해야 한다.

![image](https://user-images.githubusercontent.com/62419307/133394084-37ddd0e1-708d-4341-be05-b4ca77ff027f.png)

1. 어플리케이션이 RestTemplate를 생성하고, URI, HTTP메소드 등의 헤더를 담아 요청한다.
2. RestTemplate은 HttpMessageConverter를 사용하여 requestEntity를 요청메시지로 변환한다.
3. RestTemplate은 ClientHttpRequestFactory로 부터 ClientHttpRequest를 가져와서 요청을 보낸다.
4. ClientHttpRequest는 요청메시지를 만들어 HTTP 프로토콜을 통해 서버와 통신한다.
5. RestTemplate은 ResponseErrorHandler로 오류를 확인하고 있다면 처리로직으로 넘긴다.
6. ResponseErrorHandler는 오류가 있다면 ClientHttpResponse 에서 응답 데이터를 가져와서 처리한다.
7. RestTemplate은 HttpMessageConverter 를 이용해서 응답메시지를 java object(Class responseType) 로 변환한다.
8. 어플리케이션에 반환된다.

[참고](https://sjh836.tistory.com/141)

[참고1](https://sjh836.tistory.com/141)

[참고2](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/client/RestTemplate.html)
