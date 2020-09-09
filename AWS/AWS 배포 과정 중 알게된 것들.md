# AWS 배포 과정 중 알게된 것들 🗂

[AWS 기본 개념](https://github.com/hjyeon-n/BE_TIL/blob/master/AWS%20%EA%B0%9C%EB%85%90%20%EC%A0%95%EB%A6%AC.md)은 이제 좀 알겠지만... 

이전에 미루던 것들과 새로 마주치는 것들이 짬뽕이 돼서 더더욱 혼란스러워지는데...! 😇

좀 더 미루면 또 다 까먹을 것 같아서 빠르게 정리하도록 한다. 참된 얼은의 자세 😛 

~~사실 이미 몇 개 까먹어서 기억날 때마다 추가해야겠다...🤪~~

<br>

## JAR / WAR

사실 너무나 익숙한 이름들인데 이번 [배포 과정에서 만났을 때](https://blog.naver.com/o____ri/222084109969)는 정신이 멍해졌다... 확실히 정리해야겠다고 느낀 순간이다.

<br>

### 우선, JAR!

JAR은 **Java Archive**의 약자이다. CLASS와 같은 JAVA 리소스와 속성 파일, 라이브러리 및 액세서리 파일이 포함되어 있다. 이 데이터를 하나의 파일로 모아서 자바 플랫폼에 응용 소프트웨어나 라이브러리를 배포하기 위한 소프트웨어 패키지 파일 포맷이다. 

쉽게 말하면, JAVA 어플리케이션이 동작할 수 있도록 **자바 프로젝트를 압축한 파일**이라고 생각하면 된다. 

JAR 파일은 플랫폼에 귀속되는 점만 제외하면 WIN ZIP 파일과 동일한 구조이다.

JAR 파일은 원하는 구조로 구성이 가능하며, JDK (Java Development Kit)에 포함하고 있는 JRE(Java Runtime Environment)만 가지고도 실행이 가능하다.

<br>

#### ➕ 사실... JDK, JRE 차이도 잘 모르겠어 그리고 JVM도 설명해줘! 🙋‍♀️ 

🚀 **JVM**

JVM은 **자바 가상머신**(Java Virtual Machine)의 약자이다.

JVM은 자바 소스 코드로부터 만들어지는 자바 바이너리 파일(.class)을 실행할 수 있다. 또한 JVM은 플랫폼에 의존적이다. 

즉, Linux의 JVM과 Windows의 JVM은 다르다. 단, 컴파일된 바이너리 코드는 어떤 JVM에서도 동작시킬 수 있다.

JVM은 다음과 같은 역할을 한다.

- 바이너리 코드를 읽는다.
- 바이너리 코드를 검증한다.
- 바이너리 코드를 실행한다.
- 실행환경(Runtime Environment)의 규격을 제공한다. (필요한 라이브러리 및 기타파일)

[컴파일 과정 설명은 여기서!](https://gyoogle.dev/blog/computer-language/Java/%EC%BB%B4%ED%8C%8C%EC%9D%BC%20%EA%B3%BC%EC%A0%95.html)

<br>

**🚀 JRE**

JRE는 **자바 실행환경**(Java Runtime Environment)의 약자이다.

JRE는 JVM이 자바 프로그램을 동작시킬 때 필요한 라이브러리 파일들과 기타 파일들을 가지고 있다. 

즉,  JRE는 JVM의 실행환경을 구현했다고 할 수 있다.

자바 프로그램을 **실행**시키기 위해선 JRE를 반드시 설치해야한다. 

하지만 **자바 프로그래밍 도구**는 포함되어있지 않기 때문에 **자바 프로그래밍**을 하기 위해선 JDK가 필요하다.

<br>

**🚀 JDK**

JDK는 자바 개발도구(Java Development Kit)의 약자이다. 

JDK는 JRE + 개발을 위해 필요한 도구(javac, java등)들을 포함한다. JDK를 설치하면 JRE도 같이 설치가 된다.

![image](https://user-images.githubusercontent.com/62419307/92546678-10d69e80-f28e-11ea-9fc9-2ff2526667b3.png)

[참고](https://goodgid.github.io/Java-JDK-JRE/)

<br>

### 드디어 WAR!

WAR는 **Web Application Archive**의 약자이다. servelt / jsp 컨테이너에 배치할 수 있는 웹 어플리케이션 압축 파일 포맷이다. JSP, SERVLET, JAR, CLASS, XML, HTML, JAVASCRIPT 등 Sevlet Context 관련 파일들로 패키징 되어있다. 

WAR는 웹 응용 프로그램을 위한 포맷이기 때문에 **웹 관련 자원만 포함하고 있으며, 이를 사용하면 웹 어플리케이션을 쉽게 배포**하고 테스트할 수 있다.

원하는 구성을 만들 수 있는 JAR 포맷과 달리 WAR는 WEB-INF 및 META-INF 디렉토리로 사전 정의된 구조를 사용하며 **WAR 파일을 실행하려면 Tomcat, Weblogic 등의 웹 서버(WEB) 또는 웹 컨테이너(WAS)가 필요하다.**

✔ [여기서 WEB/WAS 비교를 확인할 수 있다!](https://github.com/hjyeon-n/BE_TIL/blob/master/%EC%9B%B9%20%EC%84%9C%EB%B2%84/%EC%9B%B9%20%EC%84%9C%EB%B2%84.md)

WAR 파일도 JAVA의 JAR 옵션을 이용해 생성하는 JAR 파일의 일종으로, 웹 어플리케이션 전체를 패키징하기 위한 JAR 파일로 생각하면 된다.

<br>

### 서비스로, EAR까지!

EAR은 **Enterprise Archive**의 약자이다. JAVA EE (Enterprise Edition)에서 쓰이는 파일 형식으로, 한 개 이상의 모듈을 단일 아카이브로 패키징하여 어플리케이션 서버에 동시에 일괄적으로 올리기 위하여 사용되는 포맷이다.

[참고](https://ifuwanna.tistory.com/224)

<br>

[jar 배포 환경을 war로 바꾸면서 에러가 생겼는데](https://blog.naver.com/o____ri/222084109969) 처음에는 JAR은 내장된 서버가 있지만, WAR은 그런 게 없으니  tomcat-embed-jasper를 추가해야 하는 건가? 해서 주석 처리된 부분을 지웠더니 잘 됐는데... 아무래도 뭐가 좀 이상해서 더 찾아보았다.

#### "tomcat-embed-jasper"

간단히 말해서 **jsp를 사용하기 위해서** 따로 추가해야 한다. 에러가 나는 상황도 분명 war 파일이 서버에 잘 올라갔는데 자꾸 WEB-INF 경로를 띄우면서 페이지를 찾을 수 없다고 뜨면서 대환장 파티가 일어났더랬다...🤯

Spring boot가 jsp를 지원하지 않아 생기는 문제였고, tomcat-embed-jasper 이를 dependency에 추가해야 비로소 jsp 파일을 찾을 수 있었다. 😭

[찾아보니, 공식 문서에서 JSP를 지원하지 않은 이유가 설명돼 있었다.](https://docs.spring.io/spring-boot/docs/2.1.5.RELEASE/reference/htmlsingle/#boot-features-jsp-limitations)

![image](https://user-images.githubusercontent.com/62419307/92549126-91e46480-f293-11ea-8618-7825dd006f31.png)

JSP 대신 Thymeleaf나 Velocity를 사용해 볼까 했는데 어쩌다보니 JSP를 사용하게 되었다... 이래서 습관이 무섭다 덜덜...

다음 토이 프로젝트를 진행하게 되면 무조건 Tymeleaf를 써봐야겠다...! 이번에도 이번 나름의 새로운 경험을 했으니까 그걸로 됐다! 😊