# JAVA의 이것저것

현재 주력 언어로 JAVA를 쓰긴 하지만 현재 쓰고 있는 자바 버전의 특징이나 신기술 등 잘 아는 게 없는 것 같아서 따로 정리해 본다! 

이 정리본도 계속해서 업데이트 예정이다! 😜

<br>

### JAVA의 설계 목표

+ 단순하지만 강력하다.
+ 객체지향적이다.
+ 분산 환경 지원
+ 견고하다.
+ 안전하다.
+ 컴퓨터 구조에 중립적이다.
+ 이식성이 있다.
+ 고성능이다.
+ 멀티스레딩 지원
+ 동적이다.

<br>

### JAVA8

JAVA8에서 새로운 변경 사항은 크게 4가지이다.

1. 람다 표현식
2. 스트림 API
3. java.time 패키지
4. 나즈혼



#### 람다 표현식 🧩

람다 표현식(lambda expression)이란 간단히 말해 **메소드를 하나의 식으로 표현**한 것이다.

**즉, 식별자 없이 실행할 수 있는 함수 표현식을 의미**하며, 따라서 익명 함수(anonymous function)라고도 한다.

 메소드를 람다 표현식으로 표현하면 클래스를 만들고 객체를 생성하지 않아도 메소드를 사용할 수 있다. 또한, 람다 표현식은 메소드의 매개변수로 전달될 수도 있고, 메소드의 결과값으로 반환될 수도 있다. 이러한 람다 표현식은 기존의 불필요한 코드를 줄여주고, 작성된 코드의 가독성을 높이는 데 그 목적이 있다. [여기](https://github.com/hjyeon-n/BE_TIL/blob/master/Spring%EC%9D%98%20%EC%9D%B4%EA%B2%83%EC%A0%80%EA%B2%83/Lambda.md)에 더 정리했다!

<br>

#### 스트림 API 🌊

자바에서는 많은 양의 데이터를 저장하기 위해서 배열이나 컬렉션을 사용한다. 또한, 이렇게 저장된 데이터에 접근하기 위해서는 반복문이나 반복자(iterator)를 사용하여 매번 코드를 작성해야 했다. 😟

하지만 이렇게 작성된 코드는 길이가 길고 가독성도 떨어지며, 코드의 재사용이 거의 불가능하다는 단점이 있다. 또한, 데이터베이스의 쿼리와 같이 정형화된 처리 패턴이 아니기 때문에 데이터마다 다른 방법으로 접근해야만 했다.

이러한 문제점을 극복하기 위해서 Java SE 8 버전부터 도입된 방법이 바로 스트림(stream) API다. 🧐

스트림 API는 **데이터를 추상화하여 다루므로, 다양한 방식으로 저장된 데이터를 읽고 쓰기 위한 공통된 방법을 제공**한다. 따라서 스트림 API를 이용하면 배열이나 컬렉션뿐만 아니라 파일에 저장된 데이터도 모두 같은 방법으로 다룰 수 있다.

<br>

#### java.time 패키지 ⏰

 JDK 1.0에서는 Date 클래스를 사용하여 날짜에 관한 처리를 수행했다. 하지만 Date 클래스는 현재 대부분의 메소드가 사용을 권장하지 않고(deprecated) 있다.

JDK 1.1부터 새롭게 제공된 Calendar 클래스는 날짜와 시간에 대한 정보를 얻을 수는 있지만, 다음과 같은 문제점을 가지고 있다.

1. Calendar 인스턴스는 불변 객체(immutable object)가 아니라서 값이 수정될 수 있다.
2. 윤초와 같은 특별한 상황을 고려하지 않는다.
3. Calendar 클래스에서는 월(month)을 나타낼 때 1월부터 12월을 0부터 11까지로 표현해야 하는 불편함이 있다.

따라서 많은 자바 개발자들은 Calendar 클래스뿐만 아니라 더 나은 성능의 Joda-Time이라는 라이브러리를 함께 사용해 왔다!

Java SE 8 버전에서는 이러한 **Joda-Time 라이브러리를 발전시킨 새로운 날짜와 시간 API인 java.time 패키지를 제공**한다.

java.time 패키지는 위와 같은 문제점을 모두 해결했으며, 다양한 기능을 지원하는 다수의 하위 패키지를 포함하고 있다.

<br>

#### 나즈혼(Nashorn) 🦾

지금까지 자바스크립트의 기본 엔진으로는 모질라의 리노(Rhino)가 사용되어 왔다. 이번 Java SE 8 버전부터는 자바스크립트의 새로운 엔진으로 오라클의 나즈혼(Nashorn)을 도입하게 된다. 나즈혼(Nashorn)은 기존에 사용되어 온 리노에 비해 **성능과 메모리 관리 면에서 크게 개선된 스크립트 엔진**이다. 