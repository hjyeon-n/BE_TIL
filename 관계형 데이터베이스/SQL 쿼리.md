# SQL 쿼리⚡

group by, having, order by 등 헷갈리는 것들이 많아 따로 정리하기로 한다! 😜

<br>

### DDL, DML, DCL
+ **DDL** : Data Definition Language
+ **DML** : Data Manipulation Language
+ **DCL** : Data Control Language
+ **TCL** : Transaction Control Language
 
<br>

### SELECT문 정의 순서 🦈

1. **SELECT**: 조회할 컬럼명 명시
2. **FROM**: 테이블명 명시
3. **WHERE**: 조건 (여러 개일 경우 AND나 OR로 묶어서 표현)
4. **GROUP BY**: 그룹화할 컬럼명 명시
5. **HAVING**: 그룹화된 데이터에 적용할 조건 명시
6. **ORDER BY**: 정렬할 기준이 되는 필드명 명시

<br>

### SELECT문 실행 순서 🐬

1. **FROM**: 조회할 테이블 확인
2. **WHERE**: 조건을 검색하여 조건에 맞는 데이터만 추출
3. **GROUP BY**: 지정된 컬럼별로 레코드를 하나로 묶어 그룹화
4. **HAVING**: 그룹화된 데이터에서 조건에 맞는 데이터만 추출
5. **SELECT**: 실제 데이터 값 출력
6. **ORDER BY**: 데이터를 정렬

이처럼, SELECT 다음으로 오는 구문은 ORDER BY밖에 없으므로, SELECT에서 만든 Alias는 ORDER BY 구문에서만 사용 가능하다.

<br>

### GROUP BY에 대해서 좀 더 알려줘! 😏

일반적으로 특정 그룹(포지션별, 팀별)별 데이터가 필요할 경우에 GROUP BY절을 그룹함수와 함께 이용한다.

**GROUP BY절 이용시, SELECT에 지정한 칼럼은 GROUP BY절에 모두 포함해야 한다.**

```
SELECT [DISTINCT] 컬럼명 [ALIAS명] 
FROM 테이블명 [WHERE 조건식] 
GROUP BY 컬럼이나 표현식;
```

➕ **그룹함수**

다중 행 함수의 일종으로 여러 행들의 그룹이 모여서 단 하나의 결과를 돌려주는 함수를 말한다.

✅ WHERE절에서는 GROUP BY를 위해 사용하는 그룹함수를 절대 사용할 수가 없다. (그래서, HAVING절 사용함) 

1. COUNT(a) : a행(row)의 개수

2. MAX(a) : a행 (row)의 최댓값

3. AVG(a) : a행 (row)의 평균값

<br>

*ex) 선수들의 포지션별 평균키는?*

> SELECT POSITION, AVG(HEIGHT)
>
> FROM PLAYER
>
> GROUP BY POSITION;

<br>

*ex)특정 팀 선수들의 포지션 별 인원은 어떻게 되는가?*

> SELECT POSITION, COUNT(PLAYER_NAME)
>
> FROM PLAYER
>
> WHERE TEAM_ID = 'K02'
>
> GROUP BY POSITION;

<br>

### HAVING은 뭐라고? 🙄

```
SELECT [DISTINCT] 컬럼명 [ALIAS명] 
FROM 테이블명 
[WHERE 조건식] 
GROUP BY 컬럼이나 표현식 
HAVING 그룹조건식;
```

➕ WHERE와 HAVING의 차이

+ **WHERE절 :** **SELECT ~ FROM절**에서 발췌된 데이터에 대한 제한조건을 부여하여 필요한 데이터만을 조회할 때 사용하는 조건절

+ **HAVING절 :** 그룹함수를 사용해 **GROUP BY절**을 사용할 때 그룹들에 대한 제한 조건이 필요하여 사용하는, 그룹에 대한 조건절

✅ 즉, WHERE은 SELECT의 조건문, HAVING은 GROUP BY의 조건문

<br>

### ORDER BY 😎

```
SELECT [DISTINCT] 컬럼명 [ALIAS명]
FROM 테이블명
[WHERE 조건식]
[GROUP BY 컬럼이나 표현식
HAVING 그룹조건식]
ORDER BY 칼럼이나 표현식[ASC 또는 DESC];
```

데이터 출력 순서를 지정해주는 절. 기본적으로 ORDER BY는 오름차순 정렬이 되어 ASC 생략이 가능하다. 내림차순의 경우, DESC다.

또한 ORDER BY절에서는 SELECT문에서 조회한다고 지정한 모든 항목을 입력가능하다.

<br>

[참고1](https://j2yes.tistory.com/entry/select%EB%AC%B8-%EC%88%9C%EC%84%9C%EC%99%80-having%EC%A0%88)

[참고2](https://pliss.tistory.com/8)
