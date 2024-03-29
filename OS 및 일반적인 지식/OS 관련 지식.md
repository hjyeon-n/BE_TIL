# OS 관련 지식 보충

### ❓ 임계구역(Critical Section)이란?

둘 이상의 스레드가 동시에 접근해서는 안되는 공유자원에 접근하는 코드의 일부.

즉, 스레드들은 동시에 임계영역에 접근할 수 없으며 한 임계구역당 하나의 스레드만이 접근 가능.

<br/>

### ❗ 임계구역을 해결하기 위한 조건

1. Mutual exclusion (상호배제)
   * 어떤 프로세스가 임계구역에서 작업중일 때, 다른 프로세스는 임계구역으로 접근할 수 없다.
2. Progress (진행)
   * 임계구역에서 작업중인 프로세스가 없다면, 진입하려는 프로세스중 하나를 적절히 선택해 구역에 진입할 수 있게 해야한다.
3. Bounded Waiting (유한대기)
   * 임계구역에 대한 진입요청 후 무한히 기다리지 않아야 한다.

<br/>

🤝동기화 기법으로는 **세마포어**와 **뮤텍스**가 있다.

<br/>

### ❓ 세마포어(Semaphore)란?

공유된 자원에 여러 개의 프로세스가 동시에 접근하면 문제가 발생할 수 있다.

이 때, 공유된 자원속 데이터는 한 번에 하나의 프로세스만 접근할 수 있도록 한 것이 Semaphore !

세마포어는 단순한 정수이다. 이것을 wait과 signal을 통해 조절하는 것이다.

* Semaphore가 0이면 이미 제한된 수의 프로세스가 임계구역에 접근해 있는 상태.
* Semaphore가 1 이상이 될 때까지 임계구역에 접근하는 다른 프로세스들은 대기해야 한다.
* Semaphore가 1 이상의 수이면, 다른 프로세스들은 임계구역에 접근 가능.

<br/>

### ❓ 뮤텍스(Mutex)란?

뮤텍스는 상호배제라는 뜻으로, 세마포어처럼 여러 프로세스들의 공유 리소스에 대한 접근을 위한 기법이다.

임계구역을 가진 스레드들의 Running Time이 서로 겹치지 않고 실행되도록 locking과 unlocking을 사용한다.

임계영역에 먼저 들어가는 스레드가 lock을 걸면, 이 스레드가 unlock을 할 때까지 다른 스레드들은 임계구역에 들어가지 못한다.

<br/>

### ❗ 세마포어와 뮤텍스의 차이점

1. 세마포어는 뮤텍스가 될 수 있지만 뮤텍스는 세마포어가 될 수 없다.
   * 뮤텍스는 상태가 0과 1 뿐인 Binary Semaphore라고 할 수 있다.
2. 세마포어는 소유할 수 없지만, 뮤텍스는 소유가 가능하며 소유주가 이에 대한 책임을 가진다.
3. 뮤텍스는 뮤텍스를 소유해야 뮤텍스를 해제할 수 있지만 세마포어는 세마포어를 소유하지 않아도 해제할 수 있다.
4. 세마포어는 파일형태로 존재하지만 뮤텍스는 프로세스 범위를 가지며 프로세스가 종료될 때 자동으로 Clean up 된다.

<br/>

💥가장 큰 차이점은 관리하는 **동기화 대상의 개수**!

뮤텍스는 동기화 대상이 하나뿐일 때, 세마포어는 하나 이상일때 사용

<br/>

### ❓ 경쟁상태(Race Condition)란?

둘 이상의 입력이나 조작이 동시에 일어나 의도하지 않은 결과를 가져오는 경우를 뜻한다.

프로세스들끼리 하나의 자원을 동시에 요청하는 경우로, 다중접근에 대한 제어가 제대로 이루어지지 않은 것.

두 개 이상의 프로세스가 공통 자원을 병행적으로 읽거나 쓸 때, 공용 데이터에 대한 접근이 어떤 순서에 이루어졌는지에 따라 실행결과가 달라지는 상황이 일어나기도 한다.

<br/>

### ❓ 문맥교환(Context Switching)이란?

CPU를 다른 프로세스가 사용하기 위해, 이전 프로세스의 상태롤 보관하고 새로운 프로세스를 적재하는 것

프로세스의 상태가 [준비 ▶ 실행] / [실행 ▶준비] / [실행 ▶ 대기] 로 전환될 때만 발생

불필요한 문맥교환은 오버헤드를 발생시키므로 방지하는것이 좋음

<br/>

🤯오버헤드란 어떤 처리를 하기 위해 소요되는 간접적인 처리 시간, 메모리 등을 뜻한다.
