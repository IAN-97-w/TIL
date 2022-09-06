# 💻 DQL

### 주요 용어

![DQL 용어](https://user-images.githubusercontent.com/105089699/184794846-6b6c784e-4c24-4910-9950-edc0bad0f52b.png)

### SQL

관계형 데이터베이스에서 데이터를 조회하거나 조작하기 위해 사용하는 표준 검색 언어로 원하는 데이터를 찾는 방법이나 절차를 기술하는게 아닌 조건을 기술하여 작성

| 분류 |     용도      |        명령어        |
| :--: | :-----------: | :------------------: |
| DQL  |  데이터 검색  |        SELECT        |
| DML  |  데이터 조작  | INSERT,UPDATE,DELETE |
| DDL  |  데이터 정의  |  CREATE,DROP,ALTER   |
| TCL  | 트랜잭션 제어 |   COMMIT,ROLLBACK    |

---

## ✏️ SELECTION

데이터를 조회한 결과를 Result Set이라고 하는데 SELECT구문에 의해 변환된 행들의 집합을 의미함  
Result Set은 0개 이상의 행이 포함될 수 있고 특정 기준에 의해 정렬 가능한 테이블의 특정 컬럼, 행, 행/컬럼 또는 여러 테이블의 특정 행/컬럼 조회 가능

### 작성법

> SELECT 컬럼 명[, 컬럼명, ...]  
> FROM 테이블 명  
> WHERE 조건식;  
> **작성시 SELECT, FROM은 필수로 작성**

- SELECT  
  조회하고자 하는 컬럼명을 기술  
  여러 컬럼을 조회하는 경우 컬럼은 쉼표로 구분하고, 마지막 컬럼 다음은 쉼표를 사용하지 않음 모든 컬럼 조회 시 컬럼 명 대신'\*' 기호 사용 가능하며 조회 결과는 기술한 컬럼 명 순으로 표시 됨

- FROM  
  조회 대상 컬럼이 포함된 테이블 명 기술

- WHERE  
  행을 선택하는 조건 기술  
  여러 개의 제한 조건을 포함할 수 있으며, 각각의 제한 조건은 논리 연산자로 연결  
  제한 조건을 만족시키는 행들만 Result Set에 포함

### SELECT 예시

- EMPLOYEE테이블의 사번, 이름, 급여 조회

```SQL
SELECT EMP_ID, EMP_NAME, SALARY
FROM EMPLOYEE;
```

- EMPLOYEE테이블의 모든 정보 조회

```SQL
SELECT *
FROM EMPLOYEE;
```

#### 컬럼 값 산술 연산

`컬럼 값에 대해 산술 연산한 결과 조회 가능`

- EMPLOYEE테이블에서 직원명, 연봉 조회

```SQL
SELECT EMP_NAME, SALARY * 12
FROM EMPLOYEE
```

#### 컬럼 별칭

`'AS 별칭'이나 "별칭", 또는 'AS "별칭"'을 기술하여 컬럼 별칭을 지을 수 있음`

```SQL
SELECT EMP_NAME AS "사원명" , SALARY * 12 연봉, SALARY*(1 + BONUS)*12 AS "보너스가 포함된 연봉"
FROM EMPLOYEE;
```

#### 리터럴

`임의로 지정한 문자열을 SELECT절에 사용하면 테이블에 존재하는 데이터처럼 활용 가능`

```SQL
SELECT EMP_ID, SALARY, '원' AS 단위
FROM EMPLOYEE;
```

**문자나 날짜 리터럴은 '' 기호 사용  
리터럴은 Result Set의 모든 행에 반복 표시 됨**

#### DISTINCT

`컬럼에 포함된 데이터 중 중복 값을 제외하고 한 번씩만 표시하고자 할 때 사용`

```SQL
SELECT DISTINCT JOB_CODE
FROM EMPLOYEE;
```

```SQL
SELECT DISTINCT DEPT_CODE, JOB_CODE -- DEPT_CODE, JOB_CODE에서 동시에 중복되는 것만 제거
FROM EMPLOYEE;
```

**DISTINCT는 한개만 사용가능**

### WHERE절

`검색할 컬럼의 조건을 설정하여 행 결정`

- EMPLOYEE테이블에서 부서코드가 D9인 직원의 이름, 부서코드 조회

```SQL
SELECT EMP_NAME, DEPT_CODE
FROM EMPLOYEE
WHERE DEPT_CODE = 'D9';
```

- EMPLOTEE테이블에서 급여가 4000000이상인 직원의 이름, 급여 조회

```SQL
SELECT EMP_NAME, SALARY
FROM EMPLOYEE
WHERE SALARY >= 40000000;
```

### 논리 연산자 : AND, OR

`여러 개의 제한 조건 결과를 하나의 논리 결과로 만들어줌`

| 연산자 |                           설명                           |
| :----: | :------------------------------------------------------: |
|  AND   |      여러 조건이 동시에 TRUE일 경우에만 TRUE값 반환      |
|   OR   | 여러 조건들 중에 어느 하나의 조건만 TRUE이면 TRUE값 반환 |
|  NOT   |         조건에 대한 반대 값으로 반환(NULL 제외)          |

- 부서코드가 'D6'이고 급여를 2000000보다 많이 받는 직원의 이름, 부서코드, 급여 조회

```SQL
SELECT EMP_NAME, DEPT_CODE, SALARY
FROM EMPLOYEE
WHERE DEPT_CODE = 'D6' AND SALARY > 2000000;
```

- 부서코드가 'D6'이거나 급여를 2000000보다 많이 받는 직원의 이름, 부서코드, 급여 조회

```SQL
SELECT EMP_NAME, DEPT_CODE, SALARY
FROM EMPLOYEE
WHERE DEPT_CODE = 'D6' OR SALARY >2000000;
```

### 연결 연산자

`'||'를 사용하여 여러 컬럼을 하나의 컬럼인 것처럼 연결하거나 컬럼과 리터럴을 연결함`

- 컬럼과 컬럼 연결

```SQL
SELECT EMP_ID||EMP_NAME||SALARY
FROM EMPLOYEE;
```

- 컬럼과 리터럴을 연결한 경우

```SQL
SELECT EMP_NAME||'의 월급은'||SALARY||'원 입니다.'
FROM EMPLOYEE;
```

### 비교 연산자

`표현식 사이의 관계를 비교하기 위해 사용하고 비교 결과는 논리 결과(TRUE/FALSE/NULL) 중 하나가 됨, 단 비교하는 두 컬럼 값/표현식은 서로 동일한 데이터 타입이어야 함`

![비교연산자](https://user-images.githubusercontent.com/105089699/184817171-a6285d08-42c2-4166-b5e8-2e852a893486.png)

#### BETWEEN AND

`비교하려는 값이 지정한 범위에 포함되면 TRUE를 리턴하는 연산자 상한 값과 하한 값의 경계도 포함됨`

- 급여를 3500000보다 많이 받고 6000000보다 적게 받는 직원 이름과 급여 조회

```SQL
SELECT EMP_NAME, SALARY
FROM EMPLOYEE
WHERE SALARY BETWEEN 35000000 AND 6000000;
```

#### LIKE

`비교하려는 값이 지정한 특정 패턴을 만족하면 TRUE를 리턴하는 연산자로 '%'와 '_'를 와일드카드로 사용`

'글자%' --> 글자로 시작하는 값(글자, 글자가 없다, 글자는...)  
'%글자' --> 글자로 끝나는 값(글자, 한글자, 두글자...)  
'%글자%' --> 글자가 포함된 값(글자, 한글자, 글자가 없다, 한글은 위대한 글자입니다...)  
'글%자' --> 글로 시작해서 자로 끝나는 값(글자, 글을 쓰자...)  
'\_' --> 한 글자(꽃, 강, 별...)  
'\_\_' --> 두 글자(이름, 빌딩, 자바, 공부...)

```SQL
-- EMPLOYEE테이블에서 이름이 전으로 시작되는 직원의 사원번호, 이름, 입사일 조회
SELECT EMP_NO, EMP_NAME, HIRE_DATE
FROM EMPLOYEE
WHERE EMP_NAME LIKE '전%';

-- EMPLOYEE테이블에서 이름에 하가 포함된 직원의 이름, 주민번호, 부서코드 조회
SELECT EMP_NAME, EMP_NO, DEPT_CODE
FROM EMPLOYEE
WHERE EMP_NAME LIKE '%하%';

-- EMPLOYEE테이블에서 전화번호 4번째 자리가 9로 시작하는 사원의 사번, 이름, 전화번호 조회
SELECT EMP_ID, EMP_NAME, PHONE
FROM EMPLOYEE
WHERE PHONE LIKE '___9%';
```

#### IS NULL / IS NOT NULL

`NULL 여부를 비교하는 연산자`

```SQL
-- EMPLOYEE테이블에서 보너스를 받지 않는 사원의 사번, 이름, 급여, 보너스 조회
SELECT EMP_ID, EMP_NAME, SALARY, BONUS
FROM EMPLOYEE
WHERE BONUS IS NULL;

-- EMPLOYEE테이블에서 보너스를 받는 사원의 사번, 이름, 급여, 보너스 조회
SELECT EMP_ID, EMP_NAME, SALARY, BONUS
FROM EMPLOYEE
WHERE BONUS IS NOT NULL;
```

#### IN

`비교하려는 값 목록에 일치하는 값이 있으면 TRUE를 반환하는 연산자`

```SQL
-- 직급 코드가 J1, J2, J3, J4인 사람들의 이름, 직급코드, 급여 조회
SELECT EMP_NAME, JOB_CODE, SALARY
FROM EMPLOYEE
WHERE JOB_CODE IN ('J1', 'J2', 'J3', 'J4');
```
