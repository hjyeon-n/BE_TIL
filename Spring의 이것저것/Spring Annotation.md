# Spring Annotation

개발을 하면 할수록 점점 annotation이 많아져서 확실히 무슨 목적으로 사용되는지, 어떤 의미인지 알기 위해서 따로 정리해 둔다! 😏

<br>

### Annotation의 용도

+ 컴파일러에게 코드 작성 문법 에러를 체크하도록 정보 제공
+ build나 batch 시에 코드를 자동으로 생성할 수 있도록 정보 제공
+ 실행 시 특정 기능을 실행하도록 정보 제공

<br>

### ➕ Reflection

Reflection은 프로그램 실행 중 자신의 구조와 동작을 검사 및 조사, 수정하는 것을 말한다. annotation 자체는 아무런 동작을 하지 않는 단순한 선언이지만 Reflection을 이용하면 annotation의 적용 여부와 엘리먼트 값을 읽고 처리할 수 있다.

<br>

### Annotation 종류 😎

#### @ComponentScan

+ @Component와 @Service, @Repository, @Controller, @Configuration이 붙은 클래스 Bean들을 찾아서 Context에 bean등록을 해 주는 Annotation
+ xml에 bean을 직접 등록하거나 위와 같이 annotation으로 간단하게 bean을 등록할 수 있다.

<br>

#### @Component

+ 개발자가 직접 작성한 클래스를 bean으로 등록하기 위한 annotation
+ `@Bean`과 다르게 `@Component`는 name이 아닌 value를 이용해 Bean의 이름을 지정한다.

```java
@Component
public class Student {
    public Student() {
        System.out.println("hi");
    }
}
```

<br>

#### @Bean

+ 개발자가 직접 제어가 불가능한 외부 라이브러리 등을 Bean으로 만들려할 때 사용되는 Annotation

```java
@Configuration
public class ApplicationConfig {    
    @Bean
    public ArrayList<String> array(){
        return new ArrayList<String>();
    }   
}
```

<br>

#### @Autowired

+ setter method, field, constructor에서 사용하며, 타입에 따라 알아서 bean을 주입해준다.
+ type을 먼저 확인하되, 찾을 수 없는 경우 name에 따라 주입한다.

✔ bean을 주입받는 방식

1. @Autowired
2. setter method
3. constructor (@AllArgsConstructor 사용) → 권장 방식!

<br>

#### @Controller, @RestController

둘 다 Spring의 Controller를 의미하지만, 차이가 있다.

<br>

**@Controller**

+ view를 반환하는 게 주목적
+ API 서비스로 사용하고 싶을 땐 @ResponseBody annotation이 따로 필요

**@RestController**

+ API 서비스로 사용하는 게 주목적
+ @RestController = @Controller + @ResponseBody

<br>

#### @Required

setter method에 적용하면 beab 생성 시 필수 property임을 알 수 있다.

<br>

#### @Qualifier("name")

@Autowired랑 같이 쓰이며, 같은 타입의 bean 객체가 있을 때 해당 id를 적어 원하는 bean이 주입될 수 있도록 하는 annotation

<br>

#### @Resource

@Autowired와 마찬가지로 Bean 객체를 주입해 주는데 차이점은 @Autowired는 타입으로, @Resource는 이름으로 연결해 준다.
