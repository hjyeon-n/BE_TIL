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
