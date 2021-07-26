# Lombok의 이것저것

Lombok(롬복)은 Annotation 방식으로 반복되는 코드 작성을 줄여주는 코드 다이어트 라이브러리다. 보통 annotation으로 작성해두면, getter, setter, toString 같은 반복 코드를 컴파일 과정에서 생성해 주는 방식으로 동작한다. 즉, 실제로는 annotation만 보이지만 실제 class 파일에는 코드가 존재한다. 🌶

[이전에도 작성한 게 있었다!](https://github.com/hjyeon-n/BE_TIL/blob/master/Spring%EC%9D%98%20%EC%9D%B4%EA%B2%83%EC%A0%80%EA%B2%83/Spring%EC%9D%98%20%EC%9D%B4%EA%B2%83%EC%A0%80%EA%B2%83.md)

<br>

+ Getter, Setter 자동 생성
  + @Getter / @Setter
  
+ 생성자 자동생성
  + @NoArgsConstructor : 파라미터가 없는 default constructor 생성
  + @AllArgsConstructor : 모든 필드 값을 파라미터로 받는 constructor 생성
  + @RequiredArgsContructor : final이나 @NotNull인 필드 값을 파라미터로 받는 constructor 생성 
  
+ @Data

  : @Getter, @Setter,  @RequiredArgsConstructor, @ToString, @EqualsAndHashCode 를 한번에 설정할 수 있음 😎