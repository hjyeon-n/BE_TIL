# NoSQL 데이터베이스 👻

### ❓ NoSQL이란?

NoSQL의 약자에 대해선 의견이 분분하지만, 보통 Not Only SQL로 해석

단순히 기존 RDBMS의 특성뿐 아니라, 다른 특성 역시 부가적으로 지원

RDBMS의 데이터베이스가 아닌 다른 형태의 데이터 저장 기술을 의미

2000년 후반 SNS의 등장으로 인해 비정형데이터를 쉽게 처리하기 위해 점점 각광받게 됨

<br/>

### ❗ NoSQL과 관계형 데이터베이스의 차이

1. 관계형 모델을 사용하지 않으며 테이블 간의 조인 기능 없음
2. 직접 프로그래밍을 해야 하는 비SQL 인터페이스를 통한 데이터 엑세스
3. 여러 대의 DB 서버를 묶어 하나의 DB를 구성 (클러스터링)
4. 관계형 데이터베이스의 특성인 ACID 미보장
5. 데이터의 스키마와 속성들을 다양하게 수용 및 동작 정의
6. 데이터베이스의 중단 없는 서비스와 자동 복구 기능지원
7. Open Source로 제공됨

[참고자료](https://www.samsungsds.com/global/ko/support/insights/1195843_2284.html)

<br/>

### ❗ NoSQL의 종류

1. Key-Value DB

   * key와 value(String, Integer, List, Hash 등)의 쌍으로 이루어진 간단한 데이터 구조
   * 분산저장 환경에 용이해 key에 대한 엑세스 속도는 빠르지만 검색에는 취약
   * Redis, Memcached 등이 있음

2. Wide Columnar Store

   * key-value 형태의 구조의 단점을 극복하가ㅣ 위해 value에 여러 개의 column 저장 가능
   * RDBMS와 유사한 형태이며, 데이터마다 다른 스키마를 가질 수 있음

   * HBase, Cassandra 등이 있음

3. Document DB

   * JSON, XML의 Documnet 형태로 데이터가 저장됨
   * Wide Column Store 처럼 스키마가 유동적

   * MongoDB, CouchDB 등이 있음

4. Graph DB

   * 데이터를 노드간의 관계로 표현함

   * Neo4j, OrientedDB 등이 있음

<br/>

### ❗ NoSQL의 장·단점

😉 장점

* RDBMS에 비해 저렴한 비용으로 분산 처리 및 병렬 처리 가능
* 비정형 데이터 구조 설계로 설계 비용 감소
* RDBMS의 join을 linking과 embedded로 구현해 성능 향상
* Big Data 처리에 효과적
* Scale out 구조를 채택해 서버 확장에 용이하며 더 많은 데이터 저장 가능
* JSON 구조를 통해 RDBMS 테이블 구조에 비해 데이터를 직관적으로 파악 가능
* Auto Sharding 지원

😣 단점

* 데이터 업데이트 중 장애가 발생하면 데이터 손실 발생 가능
* 많은 인덱스를 사용하려면 충분한 메모리가 필요함
* document base이기 때문에 복잡한 join은 어려움
* 데이터 일관성이 항상 보장되지 않음
* 분산 저장 방식이기 때문에 update가 적용되기 까지 시간이 소요됨

<br/>

🚩 용어정리

* sharding: 단일의 놀리적 데이터셋을 다수의 DB에 쪼개고 나누는 방법. 

<br/>

### ❗ MongoDB

**✔ MongoDB의 특징**

1. JSON과 유사한 문서에 데이터를 저장
2. 문서 데이터는 응용프로그램 코드의 객체에 매핑되므로 데이터 쉽게 사용 가능
3. 임시 쿼리, 인덱싱 및 실시간 집계
4. 분산 데이터베이스 이므로 고가용성, 수평확장 및 지리적 분포가 내장되어 있음
5. 무료로 사용 가능

(이 외의 특징들은 모두 앞에서 설명한 NoSQL의 특성들과 동일하다.)

<br/>

**✔ MongoDB와 일반 RDBMS의 용어들**

| MongoDB                         | RDBMS                             |
| ------------------------------- | --------------------------------- |
| 데이터베이스(Database)          | 데이터베이스(Database)            |
| 컬렉션(Collection)              | 테이블(Table)                     |
| 도큐먼트(Document)              | 레코드(Record)                    |
| 필드(Field)                     | 컬럼(Column)                      |
| 인덱스(Index)                   | 인덱스(Index)                     |
| 쿼리의 결과로 커서(Cursor) 반환 | 쿼리의 결과로 레코드(Record) 반환 |

쿼리의 결과를 클라이언트 서버의 메모리에 모두 담아두지 않아도 처리할 수 있게 하기 위해 쿼리의 결과를 커서로 변환하며 필요할 때마다 지정된 페이지 사이즈 단위로 서버로부터 전송받아 MongoDB 클라이언트 서버에 캐싱 후 유저에게 서비스 한다.

<br/>

**✔ MongoDB의 특별한 데이터 베이스들**

1. admin
   * 이 데이터베이스에 추가된 사용자는 전체 MongoDB 내의 모든 데이터베이스에 대한 권한 획득
   * 서버 전역에 걸친 모든 명령어는 이곳에서만 실행 가능 (예: DB목록 조회, 시작, 중지 등…)
2. local
   * 특정 서버에만 보관하는 정보를 담는 곳
3. config
   * sharding 정보를 저장하는데 사용됨

<br/>

**✔ MongoDB의 다양한 명령어들**

1. database 보기

   :  show dbs

2. "kong" 라는 이름의 database 선택하기

   :  use kong

3. 선택한 database의 collections들 확인하기

   :  show collections

4. "kong" collection에 document 생성하기

   :  db.kong.insert( {name:"gimkong", age:10} )

5. 데이터 검색하기

   : db.kong.find();

6. 조건을 사용해 데이터 검색하기

   : db.kong.find( {name:"gimkong"} );