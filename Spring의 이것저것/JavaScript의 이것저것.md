# JavaScript의 이것저것

자바스크립트를 종종 사용하는데 잘 모르고 막 쓰는 것 같아서 조금씩 정리해 두려고 한다! 😎

<br>

#### JavaScript와 jQuery

둘다 혼용해서 쓰길래 무슨 차이인가 했는데 jQuery는 Javascript의 라이브러리라고 생각하면 된다!

<br>

### JavaScript 변수 범위

#### 1. var

+ 중복 선언이 가능하다.

  ```javascript
  var a = 10;
  console.log(a); // 10 출력
  
  var a = 20;
  console.log(a); // 20 출력
  ```

  <br>

+ 값 재할당이 가능하다.

  ```javascript
  var a = 10; 
  a = 20; 
  
  console.log(a); // 20 출력
  ```

  <br>

+ 함수 내부에 선언된 변수만 지역변수로 한정하며, 나머지는 모두 전역변수로 간주한다.

  ```javascript
  function test() {
  	var a = 10;
  	console.log(a); // 10 출력
  }
  
  console.log(a); // ReferenceError: a is not defined
  ```

  ```javascript
  if(true) { 
  	var a = 10; 
  	console.log(a); // 10 
  } 
  
  console.log(a); // 10
  ```
  
  <br>
  
+ 변수 호이스팅이 가능

  ```javascript
  console.log(a); // undefined 
  var a = 10; 
  console.log(a); // 10
  ```

  

<br>

#### 2. let

+ 중복선언 불가능

  ```javascript
  let a = 10; 
  let a = 20; // SyntaxError: Identifier 'a' has already been declared
  ```

  <br>

+ 값 재할당 가능

  ```javascript
  let b = 10; 
  b = 20; 
  
  console.log(b); // 20
  ```

  <br>

+ 함수 내부는 물론, if문이나 for문 등의 코드 블럭에서 선언된 변수도 지역변수로 취급한다.

+ 변수 호이스팅이 불가능

<br>

#### 3. const

+ 중복선언 불가능

  ```javascript
  const a = 10; 
  const a = 20; // SyntaxError: Identifier 'a' has already been declared
  ```

  <br>

+ 값 재할당이 불가능한 상수

  ```javascript
  const c = 10; 
  c = 20; // TypeError: Assignment to constant variable.
  ```

  <br>

+ 함수 내부는 물론, if문이나 for문 등의 코드 블럭에서 선언된 변수도 지역변수로 취급한다.

<br>

[참고](https://curryyou.tistory.com/192)

