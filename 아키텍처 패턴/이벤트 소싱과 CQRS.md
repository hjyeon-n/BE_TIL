# 이벤트 소싱과 CQRS 💰

### ❓ 이벤트 소싱 (Event Sourcing) 이란?

애플리케이션의 이벤트 로그를 모두 저장하는 아키텍처 패턴

기본 개발 방법을 사용하면 현재 상태만 확인할 수 있지만, 이벤트 소싱을 이용하면 로그를 추적해 과거 상태로 재구성할 수 있음

<br/>

### ❗ 이벤트 소싱의 장점

1. 정규 데이터 구조가 단순하다.

   💰 도메인 이벤트는 단순한 구조로 저장됨

   💰 도메인 이벤트는 수정/삭제가 일어나지 않고 추가만 일어나기 때문에 경쟁 발생 ❌

2. 임피던스 불일치가 존재하지 않는다.

   💰 도메인 모델이 직렬화된 도메인 이벤트의 집합으로 저장되기 때문!

3. 신뢰할 수 있는 시스템 기록을 확보할 수 있다.

   💰 도메인 모델의 모든 변경 내역은 도메인 이벤트로 기록되기 때문

   💰 시스템에 오류가 발생하면 개발자는 오류가 발생한 시점의 도메인 모델을 복원해 오류 분석 가능

4. 메시지 중심 아키텍처에 적합하다.

   💰 도메인 모델에서 발생한 이벤트는 안정적으로 관촬되며 반드시 발행됨을 보장할 수 있음

   💰 도메인 이벤트에 담긴 메시지는 높은 설명력을 가짐

🚩 용어정리

* 임피던스 불일치란?

  : 도메인 모델을 RDBMS에 투영할 때 발생하는 다양한 구조적 문제들

<br/>

### ❓ CQRS 란?

Command and Query Responsibility Segregation의 약자

명령과 쿼리를 분리하는 패턴 (데이터를 업데이트 하는 작업과 읽는 작업을 분리하는 것)

시스템의 성능을 향상시키고, 확장성 및 보안을 극대화 할 수 있음

높은 유연성으로 인해 시스템이 진화할 수 있으며, 업데이트 명령으로 인해 도메인 수준에서 병합 충돌이 발생하지 않도록 방지함

<br/>

### ❗ CQRS의 장·단점

장점 😉

* 각각의 도메인 목적에 맞게 집중하여 개발할 수 있다.
* 변경과 조회 로직이 분리되어 각각의 복잡도는 낮아진다.
* 명령과 쿼리 파이프라인을 원하는대로 최적화 하면서 다른 요소가 깨질 위험은 거의 없다.

단점 😣

* 변경과 조회를 따로 구현하므로 코드가 더 많아진다.
* 더 많은 구현 기술이 피용해진다.
* 유지 비용이 증가한다.

<br/>

### ❗ 이벤트 소싱 + CQRS

이벤트 소싱은 이벤트 저장소가 비즈니스의 다양한 데이터 조회 요구를 수용하기 어렵다는 단점이 있다.

이런 문제를 해결하기 위해 이벤트 소싱은 항상 CQRS와 함께 활용된다. 👩🏻‍🤝‍👩🏻

둘이 함께 사용되면 도메인 모델은 비즈니스 요구에 적합한 다양한 비정규 형상을 가질 수 있다.
