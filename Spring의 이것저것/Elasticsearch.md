# Elasticsearch 🔍

TIL을 정리했을 때는 잘 모르는 개념이라 별로 중요하지 않다고 생각해서 넘겨버렸는데 요즘 자꾸 눈에 띄길래 제대로 정리해 보려고 한다! 😋

<br>

### Elasticsearch가 뭐야?

Elasticsearch는 Apache Lucene 기반의 Java 오픈소스 분산 검색 엔진을 말한다. 방대한 양의 데이터를 신속하게 거의 실시간 (NRT : Near Real Time)으로 저장, 검색, 분석이 가능하다.

검색을 위해 단독으로 사용되기도 하고, ELK 스택으로도 사용된다.

<br>

### ELK 스택...? 🙄

+ Logstash

  : 다양한 소스의 로그 또는 트랜잭션 데이터를 수집, 집계, 파싱하여 Elasticsearch로 전달

+ Elasticsearch

  : Logstash로부터 받은 데이터를 검색, 집계하여 필요한 정보 획득

+ Kibana

  : Elasticsearch의 빠른 검색을 통해 데이터 시각화 및 모니터링

<br>

### 아직도 모르겠는데...? 😵

![image](https://user-images.githubusercontent.com/62419307/133185159-0cb86bbb-e799-4076-ab80-b4cb8e904e32.png)

그렇다면 RDBMS랑 연관지어서 생각하면 된다! 조금 낯선 용어들이어도 대응되는 RDBMS 용어들을 생각하면 어렵진 않을 거다! 😼

<br>

### Elasticsearch 아키텍처와 용어 정리

![image](https://user-images.githubusercontent.com/62419307/133185043-44cdd4d9-7dff-4e64-8419-b61d6fd8293d.png)

Elasticsearch의 개념들은 앞서 봤던 것처럼 RDBMS에도 존재하는 개념들이 큰 비중을 차지한다. 이제 용어를 설명해 보겠다! 😎

1. **클러스터** (cluster)

   + Elasticsearch에서 가장 큰 시스템 단위로, 최소 하나 이상의 노드로 이루어진 노드들의 집합을 말한다. 
   + 각 클러스터는 독립적인 시스템이기 때문에 데이터 접근, 교환이 허용되지 않는다.
   + 여러 대의 서버가 하나의 클러스터를 구성하거나 한 서버가 여러 개의 클러스터를 구성할 수 있다.

   <br>

2. **노드** (node)

   : Elasticsearch를 구성하는 하나의 단위 프로세스를 의미

   + **master-eligible node**
     + 클러스터를 제어하는 마스터로 선택할 수 있는 노드
   + **Data node**
     + 데이터와 관련된 CRUD 작업과 관련있는 노드
     + CPU, 메모리 등 자원을 많이 소모하기 때문에 모니터링이 필요하다
   + **Ingest node**
     + 데이터를 변환하는 등 사전 처리 파이프라인을 실행
   + **Coordination only node**
     + data node와 master-eligible node의 일을 대신함
     + 로드밸런서와 비슷한 역할

   <br>

3. **인덱스** (Index), **샤드** (Shard), **복제** (Replica)

   + **index**
     + RDBMS의 데이터베이스와 대응하는 개념
   + **sharding**
     + 데이터를 분산해서 저장하는 방법
     + scale-out을 위해 index를 여러 shard로 쪼갠 것
   + **replica**
     + 노드를 손실했을 경우 데이터의 신뢰성을 위해 shard들을 복제
     + 또 다른 형태의 shard라고 할 수 있음

<br>
