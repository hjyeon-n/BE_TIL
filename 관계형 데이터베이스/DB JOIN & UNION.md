# DB JOIN & UNION🔗

JOIN 개념은 잘 알고는 있는데 실제 쿼리에 사용하려고 할 때 헷갈릴 때가 있어서 따로 정리해둔다! ✍

<br>

### JOIN이 뭐더라...? 🤷‍♀️

두 개 이상의 **테이블이나 데이터베이스를 연결하여 데이터를 검색**하는 방법이다. 검색하고 싶은 컬럼이 다른 테이블에 있을 경우 주로 사용하며, 여러 개의 테이블을 마치 하나의 테이블인 것처럼 활용하는 방법이다. **보통 Primary key혹은 Foreign key로 두 테이블을 연결**한다.

<br>

## INNER JOIN이랑 OUTER JOIN의 차이는 뭐야? 🙋‍♀️

### INNER JOIN

![image](https://user-images.githubusercontent.com/62419307/94098834-82087b00-fe64-11ea-91fd-f144c81725c8.png)

쉽게말해 교집합이라고 생각하면 된다. 기준 테이블과 Join한 테이블의 중복된 값을 보여준다. 결과 값은 **A 테이블과 B 테이블이 모두 가지고 있는 데이터**만 검색된다.

```
SELECT 테이블별칭.조회할컬럼, 테이블별칭.조회할컬럼 
FROM 기준 테이블 별칭 
INNER JOIN 조인테이블 별칭 ON 기준테이블 별칭.기준키 = 조인테이블별칭.기준키....
```

<br>

두 개의 테이블이 있다고 가정하자.

![image](https://user-images.githubusercontent.com/62419307/94099225-63ef4a80-fe65-11ea-8441-ef19a965c6b4.png)

1, 2는 A에만 있고, 5, 6은 B에만 있다. 3, 4는 A와 B 둘 다 있는 것을 확인할 수 있다.

이때, INNER JOIN을 하게 되면

```
select * from a INNER JOIN b on a.a = b.b; 

select a.*,b.* from a,b where a.a = b.b;
```

![image](https://user-images.githubusercontent.com/62419307/94099603-4e2e5500-fe66-11ea-8737-5e516916e75b.png)

이와 같이 교집합처럼 공통인 부분만 나오게 된다.

<br>

### OUTER JOIN

쉽게 말해 A와 B의 합집합을 말한다. OUTER JOIN에는 LEFT OUTER JOIN, RIGHT OUTER JOIN이 있다.

<br>

### LEFT OUTER JOIN

![image](https://user-images.githubusercontent.com/62419307/94099778-ad8c6500-fe66-11ea-84d8-7fcd835989ee.png)

기준 테이블의 값 + 테이블과 기준테이블의 중복된 값을 보여준다. 즉, 왼쪽 테이블을 기준으로 JOIN을 하겠다고 생각하면 된다.

결과 값은 **A테이블의 모든 데이터와 A테이블과 B테이블의 중복되는 값**이 검색된다.

```
SELECT 테이블별칭.조회할컬럼, 테이블별칭.조회할컬럼 
FROM 기준테이블 별칭 
LEFT OUTER JOIN 조인테이블 별칭 ON 기준테이블별칭.기준키 = 조인테이블별칭.기준키
```

<br>

마찬가지로 예시로 사용했던 A와 B의 LEFT OUTER JOIN의 값을 확인해 보자.

```
select * from a LEFT OUTER JOIN b on a.a = b.b; 

select a.*,b.* from a,b where a.a = b.b(+);
```

![image](https://user-images.githubusercontent.com/62419307/94100005-50dd7a00-fe67-11ea-8446-2e362b82c63c.png)

A의 모든 값과 A와 B의 공통적인 부분만 값이 나오고 B만 가지고 있는 값은 null로 나온다.

<br>

### RIGHT OUTER JOIN

![image](https://user-images.githubusercontent.com/62419307/94100092-a023aa80-fe67-11ea-8628-c2e1d4058e97.png)

LEFT OUTER JOIN의 반대이다. 오른쪽 테이블을 기준으로 JOIN을 하겠다고 생각하면 된다.

결과 값은 **B테이블의 모든 데이터와 A테이블과 B테이블의 중복되는 값**이 검색된다.

```
SELECT 테이블별칭.조회할 컬럼, 테이블별칭.조회할 컬럼 
FROM 기준테이블 별칭 
RIGHT OUTER JOIN 조인테이블 별칭 ON 기준테이블별칭.기준키 = 조인테이블별칭.기준키
```

<br>

A와 B의 RIGHT OUTER JOIN의 값을 확인해 보자.

```
select * from a RIGHT OUTER JOIN b on a.a = b.b; 

select a.*,b.* from a,b where a.a(+) = b.b;
```

![image-20200924132141535](C:\Users\jiyeon Hyun\AppData\Roaming\Typora\typora-user-images\image-20200924132141535.png)

B의 모든 값과 A와 B의 공통적인 부분만 값이 나오고 A만 가지고 있는 값은 null로 나온다.

<br>

### FULL OUTER JOIN

![image](https://user-images.githubusercontent.com/62419307/94100796-66ec3a00-fe69-11ea-83db-c74ab0fe4b7b.png)

쉽게 말해 합집합을 생각하면 된다. A테이블이 가지고 있는 데이터 , B테이블이 가지고있는 데이터 모두 검색된다.

사실상 기준테이블의 의미가 없다.

```
SELECT 테이블별칭.조회할컬럼, 테이블별칭.조회할컬럼 
FROM 기준테이블 별칭 
FULL OUTER JOIN 조인테이블 별칭 ON 기준테이블별칭.기준키 = 조인테이블별칭.기준키
```

<br>

A와 B의 FULL OUTER JOIN의 값을 확인해 보자.

```
select * from a FULL OUTER JOIN b on a.a = b.b; 
```

![image](https://user-images.githubusercontent.com/62419307/94100979-e417af00-fe69-11ea-9a61-4900c3211062.png)

<br>

### CROSS JOIN

![image](https://user-images.githubusercontent.com/62419307/94101241-78821180-fe6a-11ea-89ff-21b3be1aac79.png)

모든 경우의 수를 전부 표현해주는 방식이다. 기준 테이블이 A일 경우,  A의 데이터 한 ROW를 B 테이블 전체와 JOIN하는 방식이다.

그러니 결과값도 N * M 이 된다. 위 그림에서는 A 테이블에 데이터가 3개, B 테이블에는 데이터가 4개가 있으므로 총 12개가 검색된다.

이를 Cartesian Product라고 한다.

```
SELECT 테이블별칭.조회할컬럼, 테이블별칭.조회할컬럼 
FROM 기준테이블 별칭 
CROSS JOIN 조인테이블 별칭


SELECT 테이블별칭.조회할컬럼, 테이블별칭.조회할칼럼 
FROM 기준테이블 별칭,조인테이블 별칭
```

<br>

### SELF JOIN

![image](https://user-images.githubusercontent.com/62419307/94101726-694f9380-fe6b-11ea-8185-1a7ed901e606.png)

자기 자신과 자기 자신을 조인한다는 의미다. 하나의 테이블을 여러 번 복사해서 JOIN 한다고 생각하면 된다.

자신이 가지고 있는 컬럼을 다양하게 변형시켜 활용할 경우에 자주 사용한다.

```
SELECT 테이블별칭.조회할컬럼, 테이블별칭.조회할컬럼 
FROM 테이블 별칭, 테이블 별칭2
```

<br>

## UNION에 대해서 설명해줘! 🙆‍♀️

### UNION

UNION은 여러 개의 SELECT 문의 결과를 하나의 테이블이나 결과 집합으로 표현할 때 사용한다.

이때 각각의 SELECT 문으로 선택된 필드의 개수와 타입은 모두 같아야 하며, 필드의 순서 또한 같아야 한다.

```
SELECT 필드이름
FROM 테이블이름
UNION
SELECT 필드이름
FROM 테이블이름
```

<br>

![image](https://user-images.githubusercontent.com/62419307/94103432-a4ec5c80-fe6f-11ea-8d5f-7e1bc471322b.png)

위와 같은 테이블이 있다고 가정하자. 이 두 테이블에 대해 UNION을 실행하면

```
SELECT Name
FROM Reservation
UNION
SELECT Name
FROM Customer;
```

![image](https://user-images.githubusercontent.com/62419307/94103735-496e9e80-fe70-11ea-8700-2d70a51f2817.png)

위의 예제에서 두 SELECT 문의 결과는 하나로 합쳐져서 출력된다.

이때 두 SELECT 문의 결과에서 중복된 레코드인 '김콩'은 한 번만 표시한다.

<br>

### UNION ALL

위의 예제처럼 UNION은 DISTINCT 키워드를 따로 명시하지 않아도 기본적으로 중복되는 레코드를 제거한다.

따라서 이렇게 중복되는 레코드까지 모두 출력하고 싶다면, ALL 키워드를 사용해야 한다.

```
SELECT 필드이름
FROM 테이블이름
UNION ALL
SELECT 필드이름
FROM 테이블이름
```

<br>

마찬가지로, 두 테이블을 사용해서 UNION ALL을 실행하면

```
SELECT Name
FROM Reservation
UNION ALL 
SELECT Name
FROM Customer;
```

![image](https://user-images.githubusercontent.com/62419307/94104134-49bb6980-fe71-11ea-94e0-470858b817c2.png)

위의 예제에서 두 SELECT 문의 결과는 하나로 합쳐져서 출력된다. 이때 두 SELECT 문의 결과는 중복된 레코드까지 모두 표시한다.

<br>

### UNION이랑 JOIN의 차이는 뭐지? 🧐

![image](https://user-images.githubusercontent.com/62419307/94105532-6f963d80-fe74-11ea-850d-ccde6a6e80d2.png)

이와 같은 테이블이 있다고 가정하자.

JOIN을 먼저 실행해 보자.

```
SELECT A.ID, A.name, B.Room
FROM A
INNER JOIN B
ON A.col1 = B.col1;
```

결과는 이와 같이 나온다.

![image](https://user-images.githubusercontent.com/62419307/94105866-2c889a00-fe75-11ea-931b-6e996fc60dae.png)

<br>

즉, JOIN은 새로운 열로 결합하는 것을 의미하며 이를 **수평결합**이라고 한다.
두 테이블 결합 시, 첫 번째 테이블의 데이터는 동일한 행의 두 번째 테이블 열과 함께 표시한다.

![image](https://user-images.githubusercontent.com/62419307/94105591-95234700-fe74-11ea-9fa7-a8e9b2ca4d4a.png)

<br>

UNION을 실행하면

![image](https://user-images.githubusercontent.com/62419307/94106286-1af3c200-fe76-11ea-92d0-150b74a38eb7.png)

<br>

즉, UNION은 새로운 행으로 결합하는 것을 의미하며 이를 **수직결합**이라고 한다.
두 테이블 결합 시, 첫 번째 테이블의 데이터는 한 행 세트에 있고, 두 번째 테이블은 다른 행 세트에 있다.

![image](https://user-images.githubusercontent.com/62419307/94106427-53939b80-fe76-11ea-88cc-9b8b0f8d7178.png)

<br>

[JOIN 참고1](https://coding-factory.tistory.com/87)

[JOIN 참고2](https://stanleykou.tistory.com/entry/SQL-INNER-%EC%A1%B0%EC%9D%B8%EA%B3%BC-OUTER%EC%A1%B0%EC%9D%B8%EC%9D%B4-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94)

[UNION 참고](http://www.tcpschool.com/mysql/mysql_multipleTable_union)

[JOIN과 UNION 참고](https://syujisu.tistory.com/191)