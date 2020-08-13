# ORM 🐾

### ❓ ORM(Object Relational Mapping)이란?

데이터베이스와 객체지향 프로그래밍 언어간의 호환되지 않는 데이터를 변환 및 매핑하는 기법

예를들어, 클래스와 테이블은 기존부터 호환가능성을 두고 만들어진 것이 아니기 때문에 불일치가 발생하는데, 이를 ORM을 통해 객체간의 관계를 바탕으로 SQL문을 자동으로 생성해 불일치를 해결할 수 있다.

<br/>

### ❗ ORM의 장·단점

😉 장점

* DBMS에 대한 종속성을 줄일 수 있음
* 별도 SQL을 사용하지 않고 객체지향 프로그래밍 언어(OOP)를 그대로 사용할 수 있음
* 선언문, 할당, 종료 같은 부수적인 코드가 없거나 급격히 줄어듦
* 재사용 및 유지보수의 편리성 증가
* 모델에서 가공된 데이터를 컨트롤러에 의해 뷰와 합쳐지는 형태로 디자인 패턴을 견고하게 다질 수 있음

<br/>

😣 단점

* 자동으로 쿼리가 생성되기 때문에 직접 SQL을 사용하는 것 보다 복잡할 수 있음
* 속도나 생산성이 저하될 가능성이 있음
* 자주 사용되는 대형 쿼리는 속도를 위해 Stored Procedure를 쓰는 등 별도의 튜닝이 필요할 수 있음
* 사용하기는 편하나, 설계는 매우 신중히 해야함

<br/>

### ❗ ORM 프레임워크의 종류

1. JPA
   * ORM을 구현하는 대표적인 프레임워크인 Hibernate를 Java 표준 방식으로 정의한 것
   * Annotation을 이용한 간단한 매핑이 가능함
2. Sequelize
   * MySQL, MariaDB, SQLite 등을 지원하는 Promise에 기반한 비동기로 동작하는 Node.js ORM
3. Django ORM
   * python기반 프레임워크인 Django에서 자체적으로 지원하는 ORM

<br/>

**✔ MyBatis VS Hibernate**

* MyBatis는 Java 코드와 직접 작성한 SQL을 Mapping 시키는 것, Hibernate는 SQL을 직접 작성하지 않고 표준 인터페이스 기반으로 처리

<br/>

### ❗ 예시코드

1. ORM을 사용하지 않은 코드

   ```
   public void insertEmp(UserVO userVO){
           String query = "INSERT INTO EMP (EMPNO, ENAME, JOB, DEPTNO)
                    VALUES (?, ?, ?, ?)";
    
           PreparedStatement pstmt = conn.prepareStatement(query);
           pstmt.setString (1, empNo);
           pstmt.setString (2, empName);
           pstmt.setString (3, emmpJob);
           pstmt.setString (4, deptNo);
   
           pstmt.execute();
      }
   ```

   이 외에도 Connection, Statement, ResultSet 등 다양한 객체를 선언해 주어야함.

   가독성이 떨어지며 작업이 불편하다는 단점이 있음.

2. MyBatis를 적용한 코드

   ```
   public Integer insertComment(Comment comment) {
   	private String namespace="com.example.repository..."	
   	SqlSession sqlSession = sqlSessionFactory.openSession();
   	try {
   		int result = sqlSession.insert(namespace + ".insertComment", comment);
   		if (result > 0) {
   			sqlSession.commit();
   		}
   		return result;
   	} finally { sqlSession.close(); }
   }
   ```

   Database 처리를 위한 DAO 클래스와 Mapper 파일을 사용하는 MyBatis 방식

3. Hibernate 적용 코드

   ```
   @Service(petService)
   public class PetsitterImpl implements PetsitterService {
   	private PetRepository pr;
   	
   	@Override
   	public Pet findPetsitter(Petsitter petsitter) {
   		return pr.save(petsitter);
   	}
   }
   ```

   JPA Repository는 기본적인 CRUD 연산을 제공함

   MyBatis와 달리 쿼리를 직접 작성하지 않아도 됨

