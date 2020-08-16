# Scrypt & Bcrypt 🧊

### ❓ Scrypt Algorithm 이란?

PBKDF2 와 유사하며 Colin Percival이 2012년 설계함

다이제스트를 생성할 때 메모리 오버헤드를 갖도록 설계되어 억지 기법 공격을 시도할 때 병렬화 처리가 매우 어려움

PBKDF2보다 안전하다고 평가되며 미래에 bcrypt에 비해 더 경쟁력 있다고 여겨짐

여러 프로그래밍 언어의 라이브러리로 제공받을 수 있음

🚩 용어정리

* PBKDF2 란?

  가장 많이 사용되는 key derivation function으로, 아주 가볍고 구현하기 쉬우며 SHA와 같이 검증된 해시 함수만을 사용함

<br/>

### ❗ Scrypt 의 파라미터

```
DIGEST = scrypt(Password, Salt, N, r, p, DLen)
```

1. Password : 패스워드
2. Salt : 암호학 솔트
3. N : CPU 비용
4. r : 메모리 비용
5. p : 병렬화
6. DLen : 원하는 다이제스트 길이

<br/>

### ❗ Bcrypt Algorithm 이란?

1999년 Niels Provos와 David Mazieres가 발표하였으며 패스워드 저장을 목적으로 설계됨

현재까지 사용되는 가장 강력한 해시 매커니즘 중 하나

PBKDF2와 scrypt 와는 달리 입력값으로 72 bytes character를 사용해야 하는 제약이 있음

**✔ 사용 예시**

```
String hashed = BCrypt.hashpw(password, BCrypt.gensalt(11));

if (BCrypt.checkpw(candidate, hashed))  
    System.out.println("It matches");
else  
    System.out.println("It does not match");

```

<br/>

[참고자료](https://d2.naver.com/helloworld/318732)