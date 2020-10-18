# Spring의 이것저것🤸‍♀️

개발할 때는 일단 이 작업을 끝내야 한다는 생각에만 사로잡혀서 설정 파일이라든가 아니면 @Autowired 등 어노테이션이 무엇을 의미하는지 모르고 그냥 휙휙 가져다 쓰기에 바빴는데 이제 차근차근 정리해 보려고 한다! 👩‍🚀 

이 정리본은 특정한 목표나 포맷이 있는 게 아니라 생각날 때마다, 궁금할 때마다 채워넣어야지! 🔥

<br>

#### application.properties 📃

+ Spring Boot의 설정 파일

+ DB의 이름이나 로그인 아이디 등이 위치함

+ 클래스 경로 아래에 위치하며, Spring Boot가 자동으로 읽어옴

+ 로컬 환경, 서버 환경이 다를 경우나 기타 다른 상황들로 설정이 많아져야 할 때는 따로 분할할 수도 있다.

  [참고](https://galid1.tistory.com/664)

<br>

<hr>

#### Lombok(롬복) 🌶

**Lombok**(롬복)은 Java 라이브러리로 반복되는 `getter`, `setter`, `toString` 등의 메서드 작성 코드를 줄여주는 코드 다이어트 라이브러리이다.  롬복 설치 시에 고추 아이콘이 뜨길래 이건 또 뭔가... 싶었는데 롬복이 인도네시아어로 고추라는 뜻이라고 한다.

우리는 개발을 할 때, `Model` 클래스나 `Entity` 같은 도메인 클래스 등에는 수많은 멤버변수가 있고 이에 대응되는 getter와 setter 그리고 toString() 메서드 그리고 때에 따라서는 멤버변수에 따른 여러 개의 생성자를 만들어줘야 했다.💦

Lombok은 다이어트 라이브러리 답게! 여러가지 **어노테이션을 제공하고 이를 기반으로 코드를 컴파일과정에서 생성해 주는 방식**으로 동작하는 라이브러리이다. 즉, 코딩 과정에서는 롬복과 관련된 어노테이션만 보이고 getter와 setter 메서드 등은 보이지 않지만 실제로 컴파일된 결과물(`.class`)에는 코드가 생성되어 있다는 뜻이다!

[이 링크에서 아주 자세히 설명되어 있다!](https://dololak.tistory.com/783)

<br>

<hr>

### Maven vs Gradle 👊

스프링 개발 환경을 만들 때, Maven과 Gradle 중 빌드도구를 선택해야 하는데 솔직히 잘 모르고 처음에 사용했던 maven을 주로 사용했다. 그렇다면 빌드는 무엇이고, Maven과 Gradle 각각의 차이는 무엇이고 하는 역할은 무엇일까?

<br>

#### 그래서 빌드가 뭔데? 🙄

우리가 작성한 소스코드(.java)들과 프로젝트에서 쓰인 각각의 자원들(.xml, .jpg, .jar, .properties) 을 JVM이나 톰캣같은 WAS가 인식할 수 있는 구조로 패키징해 주는 과정을 말한다. 내가 소스코드를 어떤 구조로 개발을 하였던간에 최종적으로는 웹 어플리케이션을 서비스하기 위해서는 WAS에 배포해야 하고 WAS는 특정 규약대로 웹 어플리케이션을 인식하기 때문에 위와 같은 규칙에 맞추어 빌드를 해야 한다!

![image](https://user-images.githubusercontent.com/62419307/96080775-d0a0b680-0ef2-11eb-9811-c8dd164cb97a.png)

<br>

#### 오케이... 그러면 maven이 뭐야? 🙆‍♀️

이전에는 Ant 🐜 라는 자동화 빌드도구가 있었다. Ant는 XML을 기반으로 하는 빌드 스크립트를 작성하여 빌드를 수행하는 도구로, 라이브러리 의존 관리가 잘 되지 않는다는 단점이 있었다. 만약 A라는 jar 파일이 필요해서 설치했더니, A.jar를 실행하기 위해서는 다시 B.jar, C.jar 등 다른 파일이 필요하는 등 필요한 라이브러리를 수동으로 다운 받아야 하는 단점이 있었다.

이때 **중앙 저장소를 통한 자동 의존성 관리가 되는 maven이 등장하게 된다! 💥**

![image](https://user-images.githubusercontent.com/62419307/96081414-304b9180-0ef4-11eb-8161-a94da181a732.png)

그러면 별도로 파일을 설치할 필요없이 중앙저장소에서 해당하는 라이브러리를 가져다가 쓰면 되기 때문에 편하게 개발할 수 있다. maven도 pom.xml이라는 XML 기반의 빌드 스크립트를 사용하는데, 이곳에 **a.jar를 사용한다는것만 명시해주면 메이븐이 스스로 a.jar가 의존하는 라이브러리들까지 판단하여 다운 받는다**. 그래서 **pom.xml에 의존성을 추가하는 것!!**

➕ 뭔지도 잘 모르고 썼던 것들 또 정리! [출처](https://jeong-pro.tistory.com/168)

```
mvn install : 로컬 저장소로 배포

mvn deploy : 원격 저장소로 배포

mvn clean : 빌드 과정에서 생긴 target 디렉토리 내용 삭제
```

<br>

#### gradle이라는 것도 있던데 그건 뭐지? 🐘

gradle은 Groovy를 기반으로 한 빌드 도구이다. `Ant`와 `Maven`과 같은 이전 세대 빌드 도구의 단점을 보완하고, 장점을 취합하여 만든 오픈소스로 공개된 빌드 도구이다. Groovy는 자바 문법과 비슷해서 쉽게 익힐 수 있는 장점이 있다. 즉, 스크립트 대신에 Groovy를 이용해서 코드로서 작성할 수 있기 때문에 가독성이 높은 장점이 있다. 게다가 gradle은 maven보다 최대 100배나 빠르다고 한다! 😲

<br>

그저 익숙해서 Maven만 사용했지만, Gradle을 사용해 봐야겠다😎

[maven 참고](https://dololak.tistory.com/671)

[gradle 참고](https://bkim.tistory.com/13)

<br>

<hr>

### Spring Container 📦

DI(Dependency Injection), IOC(Inversion Of Control) 등 Spring Container가 제공하는 핵심 개념에 대해서는 알고 있지만... 정작 Spring Container가 뭐하는 친구인지 모르겠네? 🤷‍♀️

Spring Container는 **객체(bean)들의 life-cycle 관리 및 assembler 역할을 수행한다.** assembler란 말 그대로 조립기라는 뜻으로, Spring Container가 bean 설정 정보대로 DI를 수행하는 것처럼 서로 다른 두 객체를 조립하는 것! 🧩

![image](https://user-images.githubusercontent.com/62419307/96084212-a56d9580-0ef9-11eb-96ea-b440879e8c83.png)

강의자료에서 가져온 이미지☺ 그때는 그렇구나 하고 넘어갔던 게 서서히 정리되는 기분이다!

<br>

#### 근데 bean이 뭔데 자꾸 등록을 하래? ☹

bean은 스프링 컨테이너에 의해서 관리되고 애플리케이션의 핵심을 이루는 객체들을 말한다. bean 등록에는 두 가지 방법이 있다.

1. Annotation 을 이용한 자동 bean 검색 및 등록

   : 특정 package( 들 에 속한 클래스들을 모두 검색하여 특정 annotation 이 붙은 클래스들에 대해 bean 을 자동 등록하는 기능

   ✅ @Component , @Controller, @Service, @Repository, @Aspect, @Configuration

   XML 또는 Java Config 클래스에서 명시적인 bean 설정 생략 가능

   : 의존 객체나 값 주입도 annotation 으로 설정
   ✅ @Autowired , @Qualifier, @Resource, @Value

   <br>

2. XML 이나 Java config 에서 명시적 bean 설정

   ```xml
   //XML
   <bean id= "kenny" class= "com.example.springidol.Instrumentalist"/>
   ```

   ```java
   //java
   @Bean(name=“kenny")
   public Instrumentalist instr () {
   	return new Instrumentalist ();
   }
   ```

<br>

<hr>

## Servlet 💨

servlet이 자꾸 나오는데 그냥 그런 애가 있구나... 하고 넘겼다. 🤭 (수줍) 이제라도 정리해야지...!

서블릿은 웹프로그래밍에서 클라이언트의 요청을 처리하고, 그 결과를 다시 클라이언트에게  전송하는 Servlet 클래스의 구현 규칙을 지킨 자바 프로그래밍 기술을 말한다. 즉, 서블릿이란 자바로 구현 된 CGI이다.

<br>

### CGI는 또 뭐야 🥱

CGI는 특별한 라이브러리나 도구를 의미하는 것이 아니고, 별도로 제작된 웹 서버와 프로그램 간의 교환방식이다. CGI방식은 HTML의 Get 또는 Post 방법으로 클라이언트의 데이터를 환경변수로 전달하고, 프로그램의 표준 출력 결과를 클라이언트에게 전송하는 것을 말한다. 즉, **자바 어플리케이션 코딩을 하듯 웹 브라우저용 출력 화면을 만드는 방법이다**.

<br>

### Servlet Container 🐱

서블릿 컨테이너는 말 그대로 서블릿을 관리해 주는 컨테이너다. 서블릿 컨테이너는 클라이언트의 요청(Request)을 받아주고 응답(Response)할 수 있게 웹 서버와 소켓을 만들어 통신한다. 대표적인 예로 톰캣(Tomcat)이 있다. 톰캣은 실제로 웹 서버와 통신하여 JSP(자바 서버 페이지)와 Servlet이 작동하는 환경을 제공한다.

<br>

#### Servlet Container 역할 🙋‍♀️

1. **웹서버와의 통신 지원**

   서블릿 컨테이너는 서블릿과 웹서버가 손쉽게 통신할 수 있게 한다. 일반적으로 우리는 소켓을 만들고 listen, accept 등을 해야하지만 서블릿 컨테이너는 이러한 기능을 API로 제공하여 복잡한 과정을 생략한다.

2. **서블릿 생명 주기 관리**

   서블릿 클래스를 로딩하여 인스턴스화하고,  초기화 메소드를 호출하고, 요청이 들어오면 적절한 서블릿 메소드를 호출한다. 서블릿이 소멸할 때는 적절하게 Garbage Collection(가비지 컬렉션)을 진행하여 편의를 제공한다.

3. **멀티쓰레드 지원 및 관리** 

   서블릿 컨테이너는 요청이 올 때마다 새로운 자바 스레드를 하나 생성하는데, HTTP 서비스 메소드를 실행하고 나면, 쓰레드는 자동으로 소멸된다. 

4. **선언적인 보안 관리** 

   서블릿 컨테이너를 사용하면 개발자는 보안에 관련된 내용을 서블릿 또는 자바 클래스에 구현하지 않아도 된다. 일반적으로 보안관리는 XML 배포 서술자에 기록하므로, 보안에 대해 수정할 일이 생겨도 자바 소스 코드를 수정하여 다시 컴파일 하지 않아도 된다.

<br>

#### Servlet 동작 과정 🚲

![image](https://user-images.githubusercontent.com/62419307/96094685-9cd08b80-0f08-11eb-93b5-47f5420a0f66.png)

1. 사용자가 URL을 클릭하면 HTTP Request를 Servlet Container에 보낸다.
2. Servlet Container는 HttpServletRequest, HttpServletResponse 두 객체를 생성한다.
3. 사용자가 요청한 URL을 분석하여 어느 서블릿에 대한 요청인지 찾는다.
4. 컨테이너는 서블릿 service() 메소드를 호출하고, POST/GET 여부에 따라 doGet() 또는 doPost()가 호출된다.
5. doGet() 이나 doPost() 메소드는 동적인 페이지를 생성한 후 HttpServletResponse 객체에 응답을 보낸다.
6. 응답이 완료되면 HttpServletRequest, HttpServletResponse 두 객체를 소멸시킨다.

<br>

#### Servlet 생명주기 🪐

![image](https://user-images.githubusercontent.com/62419307/96124676-82a9a400-0f2e-11eb-91cf-dbc01d147c5b.png)

1. 클라이언트의 요청이 들어오면 컨테이너는 해당 서블릿이 메모리에 있는지 확인하고, 없을 경우 init()메소드를 호출하여 적재한다. init()메소드는 처음 한 번만 실행되기 때문에, 서블릿의 스레드에서 공통적으로 사용해야하는 것이 있다면 오버라이딩해서 구현한다.  실행 중 서블릿이 변경될 경우, 기존 서블릿을 파괴하고 init()을 통해 새로운 내용을 다시 메모리에 적재한다.
2. init()이 호출된 후 클라이언트의 요청에 따라서 service()메소드를 통해 요청에 대한 응답이 doGet()가 doPost()로 분기된다. 이때 서블릿 컨테이너가 클라이언트의 요청이 오면 가장 먼저 처리하는 과정으로 생성된 HttpServletRequest, HttpServletResponse에 의해 request와 response객체가 제공된다.
3. 컨테이너가 서블릿에 종료 요청을 하면 destroy()메소드가 호출되는데 마찬가지로 한 번만 실행되며, 종료 시에 처리해야하는 작업들은 destroy()메소드를 오버라이딩하여 구현하면 됩니다.

<br>

#### JSP는 왜 자꾸 나오는 거야? 🤔

서블릿을 설명하는데 JSP 개념이 계속 나왔다. 왜 그럴까? **서블릿은 자바 소스코드 속에 HTML코드가 들어가는 형태**인데, **JSP는 이와 반대로 HTML 소스코드 속에 자바 소스코드가 들어가는 구조를 갖는 웹 어플리케이션 프로그래밍 기술**이기 때문! 

+ Servlet

  : Servlet이 수정된 경우 Java 코드를 컴파일(.class 파일 생성)한 후, 동적인 페이지를 처리하기 때문에 전체 코드를 업데이트하고 다시 컴파일한 후 재배포하는 작업이 필요하다.

+ JSP

  : JSP가 수정된 경우 재배포할 필요가 없이 WAS가 알아서 처리한다. (쉬운 배포)

<br>

1. JSP만을 이용한 모델

   ![image](https://user-images.githubusercontent.com/62419307/96128382-3fe8cb80-0f30-11eb-8661-5c8561f33d75.png)

   + JSP가 사용자의 요청을 받아 Java Bean(DTO, DAO)을 호출하여 적절한 동적인 페이지를 생성한다.
   + 동작 과정
     1. JSP로 작성된 프로그램은 내부적으로 WAS에서 Servlet 파일로 변환
     2. JSP 태그를 분해하고 추출하여 다시 순수한 HTML 웹 페이지로 변환
     3. 클라이언트로 응답
   + 특징
     1. 개발 속도가 빠르다.
     2. 배우기 쉽다.
     3. 프레젠테이션 로직(View)과 비즈니스 로직(Controller)이 섞여있다.
     4. JSP 코드가 복잡해져 유지 보수가 어려워진다.

2. JSP와 Servlet을 모두 이용한 모델

   ![image](https://user-images.githubusercontent.com/62419307/96128441-52630500-0f30-11eb-8387-960e266e1223.png)

+ JSP와 Servlet을 모두 사용하여 프레젠테이션 로직(View)과 비즈니스 로직(Controller)을 분리한다.
+ View(보여지는 부분)는 HTML이 중심이 되는 JSP를 사용
+ Controller(다른 자바 클래스에 데이터를 넘겨주는 부분)는 Java 코드가 중심이 되는 Servlet을 사용
+ Model은 Java Beans로, DTO와 DAO를 통해 Mysql과 같은 Data Storage에 접근

<br>

➕ **JSP와 Thymleaf의 차이**

**Thymeleaf**

Thymeleaf는 HTML, XML, JavaScript, CSS 및 일반 텍스트를 처리 할 수 있는 웹 및 독립형 환경에서 사용할 수 있는 Java 템플릿 엔진이다.  Thymeleaf는 html파일을 가져와서 파싱해서 분석 후, 정해진 위치에 데이터를 치환해서 웹 페이지를 생성한다.

**JSP**

JSP는 서블릿으로 변환되어 실행이 된다. JSP 내에서 자바 코드를 사용할 수도 있다. (다만, 요즘은 지양하는 방식이다) Thymeleaf는 자바코드를 사용할 수 없고, jsp처럼 커스텀 태그와 같은 기능도 없다.

[참고1](https://mangkyu.tistory.com/14) / [참고2](https://12bme.tistory.com/555) / [참고3](https://gmlwjd9405.github.io/2018/11/04/servlet-vs-jsp.html) / [참고4](https://offbyone.tistory.com/410)

<br>

<hr>

### Ajax란? ✨

JavaScript의 라이브러리중 하나이며, Asynchronous Javascript And Xml(비동기식 자바스크립트와 xml)의 약자이다. 

브라우저가 가지고있는 XMLHttpRequest 객체를 이용해서 전체 페이지를 새로 로드하지 않고도 페이지의 일부만을 위한 데이터를 로드하는 기법이며, **JavaScript를 사용한 비동기 통신, 클라이언트와 서버 간에 XML 데이터를 주고받는 기술**이다.

즉, 쉽게 말하자면 **자바스크립트를 통해서 서버에 데이터를 요청하는 것**이다.

<br>

#### 어떻게 그게 가능한 거야? 🔎

기본적으로 HTTP 프로토콜은 클라이언트 쪽에서 Request를 보내고 서버 쪽에서 Response를 받으면 이어졌던 연결이 끊기게 되어있다. 그래서 화면의 내용을 갱신하기 위해서는 다시 request를 하고 response를 하며 페이지 전체를 갱신하게 된다. 하지만 이렇게 할 경우, 엄청난 자원낭비와 시간낭비를 초래할 수 있다.

AJAX는 HTML 페이지 전체가 아닌 일부분만 갱신할 수 있도록 XMLHttpRequest객체를 통해 서버에 request한다. 이 경우, **JSON이나 XML형태로 필요한 데이터만 받아 갱신하기 때문에 그만큼의 자원과 시간을 아낄 수 있다.**

<br>

#### 어떻게 동작시키지? 🧐

1. XMLHttpRequest Object를 만든다.
   - 브라우저에게 request를 보낼 준비를 시키는 과정
   - 이를 위해서 필요한 method를 갖춘 object가 필요함
2. callback 함수를 만든다.
   - 서버에서 response가 왔을 때 실행시키는 함수
   - HTML 페이지를 업데이트 함
3. Open a request
   - 서버에서 response가 왔을 때 실행시키는 함수
   - HTML 페이지를 업데이트 함
4. send the request

[참고](https://velog.io/@surim014/AJAX%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80)

<br>

<hr>

#### Spring Cloud ☁

![image](https://user-images.githubusercontent.com/62419307/96130957-90adf380-0f33-11eb-8c2c-212186a19689.png)

우선, [MSA에 대한 이해가 필요하다!](https://github.com/hjyeon-n/BE_TIL/blob/master/%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98%20%ED%8C%A8%ED%84%B4/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%20%EC%84%9C%EB%B9%84%EC%8A%A4.md)

Spring Cloud는 분산 시스템에서 공통적인 패턴(구성 관리, 서비스 검색, 지능형 라우팅, 마이크로 프록시 등 )을 모아 신속하게 구축할 수 있는 도구를 스프링 라이브러리 형태로 제공한다. 

따라서 개발자는 분산 시스템에서 필요한 부분들에 대한 부담을 덜고 충실하게 서비스의 기능을 구현하는 것에 충실할 수 있다. 또한 특정 벤더(AWS, Cloud Foundry 등)에 종속적이지 않기 때문에 다양한 분산 환경에서 잘 작동한다. 

[자세한 내용은 여기서!](https://lion-king.tistory.com/m/entry/Spring-Boot-Spring-Cloud-MSA-2-Spring-Cloud%EB%9E%80-%EA%B0%84%EB%9E%B5%ED%95%9C-%EC%86%8C%EA%B0%9C?category=855644)

<br>

#### Spring WebFlux 😎

Spring MVC 는 Java EE의 Servlet Spec에 기반하여 만들어졌고 본질적으로 Blocking + 동기방식이다. 이와는 달리 Spring Webflux는 Non Blocking + 비동기 방식이므로 Spring MVCs의 멀티 스레드 방식보다 성능이 우수하다. 

<br>

#### 동기와 비동기? blocking과 non blocking? 👀

> 동기와 비동기 = 함수가 바로 리턴되는지 여부
>
> 블록킹과 논블록킹 = 백그라운드 작업 여부를 확인하는가 여부

동기-블록킹 방식은 함수를 호출하면 백그라운드 작업이 완료되었는지 계속 확인하고 완료되면 함수가 리턴되는 구조이고, 비동기-논 블록킹 방식은 함수를 호출하고 백그라운드 작업이 끝났는지 확인하지 않고 리턴을 하고 바로 다른 작업을 한다. 백그라운드 작업의 종료 여부는 이벤트로 수신한다. Webflux는 비동기-논블록킹 방식이다!

[참고](https://hyunsoori.tistory.com/6?category=848670)

<br>

<hr>

#### @RestController와 @Controller의 차이 😜

전통적인 Spring MVC의 컨트롤러인 @Controller와 Restuful 웹서비스의 컨트롤러인 @RestController의 주요한 차이점은 HTTP Response Body가 생성되는 방식이다.

<br>

@Controller에서 View를 전달하는 방법

![image](https://user-images.githubusercontent.com/62419307/96359771-997c1080-1151-11eb-9a95-f2e9ce9b364f.png)

1. Client는 URI 형식으로 웹 서비스에 요청을 보낸다.
2. Mapping되는 Handler와 그 Type을 찾는 DispatcherServlet이 요청을 인터셉트한다.
3. Controller가 요청을 처리한 후에 응답을 DispatcherServlet으로 반환하고, DispatcherServlet은 View를 사용자에게 반환한다.

<br>

@Controller에서 data를 전달하는 방법

Spring MVC의 컨트롤러에서도 Data를 반환해야 하는 경우도 있다! Spring MVC의 컨트롤러에서는 데이터를 반환하기 위해 @ResponseBody 어노테이션을 활용한다.

![image](https://user-images.githubusercontent.com/62419307/96359790-cfb99000-1151-11eb-900d-43f73caee01d.png)

1. Client는 URI 형식으로 웹 서비스에 요청을 보낸다.
2. Mapping되는 Handler와 그 Type을 찾는 DispatcherServlet이 요청을 인터셉트한다.
3. @ResponseBody를 사용하여 Client에게 Json 형태로 데이터를 반환한다.

<br>

@RestController는 Spring MVC Controller에 @ResponseBody가 추가된 것이다. RestController의 주용도는 Json 형태로 객체 데이터를 반환하는 것이다.

![image](https://user-images.githubusercontent.com/62419307/96359820-14ddc200-1152-11eb-9068-4fb4557447d4.png)

1. Client는 URI 형식으로 웹 서비스에 요청을 보낸다.
2. Mapping되는 Handler와 그 Type을 찾는 DispatcherServlet이 요청을 인터셉트한다.
3. RestController는 해당 요청을 처리하고 데이터를 반환한다.

[참고](https://mangkyu.tistory.com/49)

<br>

<hr>

#### Forward와 Redirect의 차이 😲

사실 이미 알고 있기는 한데, 누가 물어보면 제대로 답을 하지 못할 것 같아서 다시 한 번 정리한다!

**Forward**

Forward는 Web Container 차원에서 페이지의 이동만 존재한다. 실제로 웹 브라우저는 다른 페이지로 이동했음을 알 수 없다. 그렇기 때문에 웹 브라우저에는 최초에 호출한 URL이 표시되고, 이동한 페이지의 URL 정보는 확인할 수 없다. 또한 현재 실행 중인 페이지와 forward에 의해 호출될 페이지는 Request 객체와 Response 객체를 공유한다.

![image](https://user-images.githubusercontent.com/62419307/96359933-02b05380-1153-11eb-96e1-02e75dad84a2.png)

만약 사용자가 실수 혹은 고의로 글쓰기 응답 페이지에서 새로고침을 누른다면, 요청 정보가 그대로 살아있기 때문에 요청이 여러 번 전달되어 동일한 게시물이 여러 번 등록될 수 있다. 그렇기 때문에 게시판을 제작하는 과정에서는 시스템에 변화가 생기지 않는 단순 조회 요청(글 목록 보기, 검색)의 경우일 때 forward로 응답하는 것이 바람직하다.

<br>

Redirect는 Web Container로 명령이 들어오면, 웹 브라우저에게 다른 페이지로 이동하라고 명령을 내린다. 그러면 웹 브라우저는 URL을 지시된 주소로 바꾸고 해당 주소로 이동한다. 다른 웹 컨테이너에 있는 주소로 이동하며 새로운 페이지에서는 Request와 Response객체가 새롭게 생성된다.

![image](https://user-images.githubusercontent.com/62419307/96359984-88340380-1153-11eb-9679-d4b81955d686.png)

게시판을 작성하는 과정이라고 할 때, redirect를 사용하여 응답 페이지를 부르면 사용자가 실수 혹은 고의로 글쓰기 응답 페이지에서 새로고침을 누른다고 하더라도, 처음의 요청 정보는 존재하지 않으므로 게시물이 여러 번 등록되지 않는다. 그렇기 때문에 시스템에 변화가 생기는 요청(회원가입, 글쓰기 등)의 경우에는 redirection을 사용하는 것이 바람직하다.

[참고](https://mangkyu.tistory.com/51)

