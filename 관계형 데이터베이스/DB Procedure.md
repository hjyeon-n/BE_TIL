# DB Procedure

### PL/SQL

Oracle's Procedure Language extension to SQL 의 약자로, 절차적 프로그래밍 언어의 기능들을 추가하여 SQL의 단점을 보완한다. SQL의 데이터 검색 및 조작 능력과 절차적 언어의 프로그래밍 능력을 결합한 것이라고 생각하면 쉽다.

<br>

+ SQL

  : 선언적(declarative) 언어로, 질의, DML문, DDL문 등을 작성하는 데 사용됨

+ PL/SQL

  : 절차적(procedural) 언어로, program blocks, triggers, functions, procedures, packages 등을 정의하는 데 사용됨

<br>

#### PL/SQL의 장점

1. Tight integration with SQL
2. High performance
3. Portability
4. Scalability
5. Manageability

<br>

#### PL/SQL 프로그램 유형

+ 저장 프로시저 (Stored Procedures)
  +  생성 후 데이터베이스 내에 저장됨
  + 사용자가 호출하여 실행
+ 저장 함수(Stored Functions)
  + 저장 프로시저와 유사하나 처리 결과를 사용자에게 반환함
+ 트리거(Triggers)
  + 저장 프로시저의 일종
  + DML 문이 특정 table에 대해 수행될 때 자동적으로 실행됨
  + 살행하는 주체가 DBMS

<br>

#### PL/SQL Block의 구조

+ DECLARE (선언부)

  + 변수 이름과 변수 타입을 선언

    ![image](https://user-images.githubusercontent.com/62419307/123546069-1ad27b00-d796-11eb-9a57-29a6f459a516.png)

+ BEGIN (실행부)

  + 제어문, 반복문 등 로직을 기술할 수 있는 부분

    ![image](https://user-images.githubusercontent.com/62419307/123546278-e4e1c680-d796-11eb-844e-3e00a7270166.png)

  

+ EXCEPTION

  + 예외처리 부분

+ END

  + 실행 종료

    ![image](https://user-images.githubusercontent.com/62419307/123546356-368a5100-d797-11eb-81b2-7b4566c8f39d.png)

  
BEGIN, END는 필수로 작성해야 하는 부분이다.
  
