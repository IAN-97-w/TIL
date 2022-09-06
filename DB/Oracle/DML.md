# 💻DML

테이블에 값을 삽입(INSERT), 삭제(DELETE), 수정(UPADTE) 하는 데이터 조작 언어

## ✏️ INSERT

---

테이블에 새로운 행을 추가하는 구문

INSERT 예시

```SQL
INSERT INTO EMPLOYEE (EMP_ID, EMP_NAME, EMP_NO, EMAIL, PHONE, DEPT_CODE,
                      JOB_CODE, SAL_LEVEL, SALARY, BONUS, MANAGER_ID,
                      HIRE_DATE, ENT_DATE, ENT_YN)
VALUES(900, '장채현', '901123-1080503', 'jang_ch@kh.or.kr', '01055569512', 'D1', 'J8',
       'S3', 4300000, 0.2, '200', SYSDATE, NULL, DEFAULT);

-- 모든 컬럼에 INSERT 하고 싶은 경우 컬럼 명 생략 가능. (단, 컬럼의 순서를 지켜서 VALUES에 값 기입)
INSERT INTO EMPLOYEE
VALUES(900, '장채현', '901123-1080503', 'jang_ch@kh.or.kr', '01055569512', 'D1', 'J8',
       'S3', 4300000, 0.2, '200', SYSDATE, NULL, DEFAULT);
```

INSERT 예시2 (SUBQUERY 이용)

```SQL
CREATE TABLE EMP_01(
    EMP_ID NUMBER,
    EMP_NAME VARCHAR2(30),
    DEPT_TITLE VARCHAR2(20)
);

-- INSERT 시 VALUES 대신 서브쿼리 이용 가능

INSERT INTO EMP_01(
    SELECT EMP_ID, EMP_NAME, DEPT_TITLE
    FROM EMPLOYEE
    LEFT JOIN DEPARTMENT ON (DEPT_CODE = DEPT_ID)
);
```

## ✏️ INSERT ALL

---

INSERT 시 서브쿼리가 사용하는 테이블이 같은 경우  
두 개 이상의 테이블에 INSERT ALL을 이용하여 한 번에 삽입 가능  
단, 각 서브쿼리의 조건절이 같아야 함

INSERT ALL 예시

```SQL
CREATE TABLE EMP_DEPT_D1
AS SELECT EMP_ID, EMP_NAME, DEPT_CODE, HIRE_DATE
   FROM EMPLOYEE
   WHERE 1 = 0;  -- 구조만 생성

CREATE TABLE EMP_MANAGER
AS SELECT EMP_ID, EMP_NAME, MANAGER_ID
   FROM EMPLOYEE
   WHERE 1 = 0;

-- EMP_DEPT_D1테이블에 EMPLOYEE테이블에 있는 부서코드가 D1인 직원을 조회하여 사번, 이름 ,소속부소, 입사일 삽입
-- EMP_MANAGER테이블에 EMPLOYEE테이블에 있는 부서코드가 D1인 직원을 조회하여 사번, 이름, 관리자 사번 삽입

INSERT ALL
INTO EMP_DEPT_D1 VALUES(EMP_ID, EMP_NAME, DEPT_CODE, HIRE_DATE)
INTO EMP_MANAGER VALUES(EMP_ID, EMP_NAME, MANAGER_ID)
    SELECT EMP_ID, EMP_NAME, DEPT_CODE, HIRE_DATE, MANAGER_ID
    FROM EMPLOYEE
    WHERE DEPT_CODE = 'D1';
```

INSERT ALL 예시2

```SQL
CREATE TABLE EMP_OLD
AS SELECT EMP_ID, EMP_NAME, HIRE_DATE, SALARY
   FROM EMPLOYEE
   WHERE 1 = 0;

CREATE TABLE EMP_NEW
AS SELECT EMP_ID, EMP_NAME, HIRE_DATE, SALARY
   FROM EMPLOYEE
   WHERE 1= 0;

-- EMPLOYEE테이블의 입사일 기준으로 2000년 1월 1일 이전에 입사한 사원의 사번, 이름, 입사일, 급여는 EMP_OLD테이블에 삽입,
-- 그 후 입사하 사원의 정보는 EMP_NEW 테이블에 삽입

-- INSERT ALL문에 조건(WHEN)을 추가하여 조건에 맞는 행만 테이블에 추가
INSERT ALL
WHEN HIRE_DATE < '2000/01/01' THEN
    INTO EMP_OLD VALUES(EMP_ID, EMP_NAME, HIRE_DATE, SALARY)
WHEN HIRE_DATE >= '2000/01/01' THEN
    INTO EMP_NEW VALUES(EMP_ID, EMP_NAME, HIRE_DATE, SALARY)
SELECT EMP_ID, EMP_NAME, HIRE_DATE, SALARY
FROM EMPLOYEE;
```

## ✏️ UPDATE

테이블에 기록된 컬럼 값을 수정하는 구문으로 테이블 전체 행 개수는 변화 없음

UPDATE 예시

```SQL
CREATE TABLE DEPT_COPY
AS SELECT * FROM DEPARTMENT;

UPDATE DEPT_COPY
SET DEPT_TITLE = ‘전략기획팀’
WHERE DEPT_ID = ‘D9’;
```

UPDATE 예시2 (SUBQUERY 이용)

```SQL
CREATE TABLE EMP_SALARY
AS SELECT EMP_ID, EMP_NAME, DEPT_CODE,  SALARY, BONUS
FROM EMPLOYEE;

-- 방명수 사원의 급여와 보너스율을 유재식 사원과 동일하게 변경
UPDATE EMP_SALARY
SET (SALARY, BONUS) = (SELECT SALARY, BINUS
                       FROM EMP_SALARY
                       WHERE EMP_NAME = '유재식')
WHERE EMP_NAME = '방명수';

-- 노옹철, 전형돈, 정중하, 하동운 사원의 급여, 보너스를 유재식 사원과 같은 값으로 변경
UPDATE EMP_SALARY
SET (SALARY, BONUS) = (SELECT SALARY, BINUS
                       FROM EMP_SALARY
                       WHERE EMP_NAME = '유재식')
WHERE EMP_NAME IN ('노옹철', '전형돈', '정중하', '하동운');
```

## ✏️ DELETE

테이블의 행을 삭제하는 구문으로 테이블의 행 개수가 줄어듦

DELETE 예시

```SQL
DELETE FROM EMPLOYEE; -- 테이블 전체 데이터 삭제

DELETE FROM EMPLOYEE
WHERE EMP_NAME = '강건강'; -- 특정 행 삭제
```

### 제약조건 비활성화

삭제 시 FOREIGN KEY 제약조건으로 컬럼 삭제가 불가능한 경우 제약조건을 비활성화 할 수 있음

예시

```SQL
DELETE FROM DEPARTMENT
WHERE DEPT_ID = ‘D1’;

ALTER TABLE EMPLOYEE
DISABLE CONSTRAINT EMP_DEPTCODE_FK CASCADE; -- 제약조건 비활성화

DELETE FROM DEPARTMENT
WHERE DEPT_ID = ‘D1’;

ALTER TABLE EMPLOYEE
ENABLE CONSTRAINT EMP_DEPTCODE_FK; -- 제약조건 활성화
```

## ✏️ TRUNCATE

테이블 전체 행 삭제 시 사용하며 DELETE보다 수행 속도가 빠르고 ROLLBACK을 통해 복구 불가능  
또한 DELETE와 마찬가지로 FOREIGN KEY 제약조건일 때는 적용 불가능하기 때문에 제약 조건을 비활성화 해야 삭제할 수 있음

```SQL
TRUNCATE TABLE EMP_SALARY;
SELECT * FROM EMP_SALARY;   -- 모든 컬럼이 삭제되긴 하지만 테이블의 구조는 남아있음

ROLLBACK;   -- ROLLBACK 후에도 컬럼이 복구되지 않음
```
