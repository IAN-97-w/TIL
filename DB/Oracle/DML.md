# ๐ปDML

ํ์ด๋ธ์ ๊ฐ์ ์ฝ์(INSERT), ์ญ์ (DELETE), ์์ (UPADTE) ํ๋ ๋ฐ์ดํฐ ์กฐ์ ์ธ์ด

## โ๏ธ INSERT

---

ํ์ด๋ธ์ ์๋ก์ด ํ์ ์ถ๊ฐํ๋ ๊ตฌ๋ฌธ

INSERT ์์

```SQL
INSERT INTO EMPLOYEE (EMP_ID, EMP_NAME, EMP_NO, EMAIL, PHONE, DEPT_CODE,
                      JOB_CODE, SAL_LEVEL, SALARY, BONUS, MANAGER_ID,
                      HIRE_DATE, ENT_DATE, ENT_YN)
VALUES(900, '์ฅ์ฑํ', '901123-1080503', 'jang_ch@kh.or.kr', '01055569512', 'D1', 'J8',
       'S3', 4300000, 0.2, '200', SYSDATE, NULL, DEFAULT);

-- ๋ชจ๋  ์ปฌ๋ผ์ INSERT ํ๊ณ  ์ถ์ ๊ฒฝ์ฐ ์ปฌ๋ผ ๋ช ์๋ต ๊ฐ๋ฅ. (๋จ, ์ปฌ๋ผ์ ์์๋ฅผ ์ง์ผ์ VALUES์ ๊ฐ ๊ธฐ์)
INSERT INTO EMPLOYEE
VALUES(900, '์ฅ์ฑํ', '901123-1080503', 'jang_ch@kh.or.kr', '01055569512', 'D1', 'J8',
       'S3', 4300000, 0.2, '200', SYSDATE, NULL, DEFAULT);
```

INSERT ์์2 (SUBQUERY ์ด์ฉ)

```SQL
CREATE TABLE EMP_01(
    EMP_ID NUMBER,
    EMP_NAME VARCHAR2(30),
    DEPT_TITLE VARCHAR2(20)
);

-- INSERT ์ VALUES ๋์  ์๋ธ์ฟผ๋ฆฌ ์ด์ฉ ๊ฐ๋ฅ

INSERT INTO EMP_01(
    SELECT EMP_ID, EMP_NAME, DEPT_TITLE
    FROM EMPLOYEE
    LEFT JOIN DEPARTMENT ON (DEPT_CODE = DEPT_ID)
);
```

## โ๏ธ INSERT ALL

---

INSERT ์ ์๋ธ์ฟผ๋ฆฌ๊ฐ ์ฌ์ฉํ๋ ํ์ด๋ธ์ด ๊ฐ์ ๊ฒฝ์ฐ  
๋ ๊ฐ ์ด์์ ํ์ด๋ธ์ INSERT ALL์ ์ด์ฉํ์ฌ ํ ๋ฒ์ ์ฝ์ ๊ฐ๋ฅ  
๋จ, ๊ฐ ์๋ธ์ฟผ๋ฆฌ์ ์กฐ๊ฑด์ ์ด ๊ฐ์์ผ ํจ

INSERT ALL ์์

```SQL
CREATE TABLE EMP_DEPT_D1
AS SELECT EMP_ID, EMP_NAME, DEPT_CODE, HIRE_DATE
   FROM EMPLOYEE
   WHERE 1 = 0;  -- ๊ตฌ์กฐ๋ง ์์ฑ

CREATE TABLE EMP_MANAGER
AS SELECT EMP_ID, EMP_NAME, MANAGER_ID
   FROM EMPLOYEE
   WHERE 1 = 0;

-- EMP_DEPT_D1ํ์ด๋ธ์ EMPLOYEEํ์ด๋ธ์ ์๋ ๋ถ์์ฝ๋๊ฐ D1์ธ ์ง์์ ์กฐํํ์ฌ ์ฌ๋ฒ, ์ด๋ฆ ,์์๋ถ์, ์์ฌ์ผ ์ฝ์
-- EMP_MANAGERํ์ด๋ธ์ EMPLOYEEํ์ด๋ธ์ ์๋ ๋ถ์์ฝ๋๊ฐ D1์ธ ์ง์์ ์กฐํํ์ฌ ์ฌ๋ฒ, ์ด๋ฆ, ๊ด๋ฆฌ์ ์ฌ๋ฒ ์ฝ์

INSERT ALL
INTO EMP_DEPT_D1 VALUES(EMP_ID, EMP_NAME, DEPT_CODE, HIRE_DATE)
INTO EMP_MANAGER VALUES(EMP_ID, EMP_NAME, MANAGER_ID)
    SELECT EMP_ID, EMP_NAME, DEPT_CODE, HIRE_DATE, MANAGER_ID
    FROM EMPLOYEE
    WHERE DEPT_CODE = 'D1';
```

INSERT ALL ์์2

```SQL
CREATE TABLE EMP_OLD
AS SELECT EMP_ID, EMP_NAME, HIRE_DATE, SALARY
   FROM EMPLOYEE
   WHERE 1 = 0;

CREATE TABLE EMP_NEW
AS SELECT EMP_ID, EMP_NAME, HIRE_DATE, SALARY
   FROM EMPLOYEE
   WHERE 1= 0;

-- EMPLOYEEํ์ด๋ธ์ ์์ฌ์ผ ๊ธฐ์ค์ผ๋ก 2000๋ 1์ 1์ผ ์ด์ ์ ์์ฌํ ์ฌ์์ ์ฌ๋ฒ, ์ด๋ฆ, ์์ฌ์ผ, ๊ธ์ฌ๋ EMP_OLDํ์ด๋ธ์ ์ฝ์,
-- ๊ทธ ํ ์์ฌํ ์ฌ์์ ์ ๋ณด๋ EMP_NEW ํ์ด๋ธ์ ์ฝ์

-- INSERT ALL๋ฌธ์ ์กฐ๊ฑด(WHEN)์ ์ถ๊ฐํ์ฌ ์กฐ๊ฑด์ ๋ง๋ ํ๋ง ํ์ด๋ธ์ ์ถ๊ฐ
INSERT ALL
WHEN HIRE_DATE < '2000/01/01' THEN
    INTO EMP_OLD VALUES(EMP_ID, EMP_NAME, HIRE_DATE, SALARY)
WHEN HIRE_DATE >= '2000/01/01' THEN
    INTO EMP_NEW VALUES(EMP_ID, EMP_NAME, HIRE_DATE, SALARY)
SELECT EMP_ID, EMP_NAME, HIRE_DATE, SALARY
FROM EMPLOYEE;
```

## โ๏ธ UPDATE

ํ์ด๋ธ์ ๊ธฐ๋ก๋ ์ปฌ๋ผ ๊ฐ์ ์์ ํ๋ ๊ตฌ๋ฌธ์ผ๋ก ํ์ด๋ธ ์ ์ฒด ํ ๊ฐ์๋ ๋ณํ ์์

UPDATE ์์

```SQL
CREATE TABLE DEPT_COPY
AS SELECT * FROM DEPARTMENT;

UPDATE DEPT_COPY
SET DEPT_TITLE = โ์ ๋ต๊ธฐํํโ
WHERE DEPT_ID = โD9โ;
```

UPDATE ์์2 (SUBQUERY ์ด์ฉ)

```SQL
CREATE TABLE EMP_SALARY
AS SELECT EMP_ID, EMP_NAME, DEPT_CODE,  SALARY, BONUS
FROM EMPLOYEE;

-- ๋ฐฉ๋ช์ ์ฌ์์ ๊ธ์ฌ์ ๋ณด๋์ค์จ์ ์ ์ฌ์ ์ฌ์๊ณผ ๋์ผํ๊ฒ ๋ณ๊ฒฝ
UPDATE EMP_SALARY
SET (SALARY, BONUS) = (SELECT SALARY, BONUS
                       FROM EMP_SALARY
                       WHERE EMP_NAME = '์ ์ฌ์')
WHERE EMP_NAME = '๋ฐฉ๋ช์';

-- ๋ธ์น์ฒ , ์ ํ๋, ์ ์คํ, ํ๋์ด ์ฌ์์ ๊ธ์ฌ, ๋ณด๋์ค๋ฅผ ์ ์ฌ์ ์ฌ์๊ณผ ๊ฐ์ ๊ฐ์ผ๋ก ๋ณ๊ฒฝ
UPDATE EMP_SALARY
SET (SALARY, BONUS) = (SELECT SALARY, BONUS
                       FROM EMP_SALARY
                       WHERE EMP_NAME = '์ ์ฌ์')
WHERE EMP_NAME IN ('๋ธ์น์ฒ ', '์ ํ๋', '์ ์คํ', 'ํ๋์ด');
```

## โ๏ธ DELETE

ํ์ด๋ธ์ ํ์ ์ญ์ ํ๋ ๊ตฌ๋ฌธ์ผ๋ก ํ์ด๋ธ์ ํ ๊ฐ์๊ฐ ์ค์ด๋ฆ

DELETE ์์

```SQL
DELETE FROM EMPLOYEE; -- ํ์ด๋ธ ์ ์ฒด ๋ฐ์ดํฐ ์ญ์ 

DELETE FROM EMPLOYEE
WHERE EMP_NAME = '๊ฐ๊ฑด๊ฐ'; -- ํน์  ํ ์ญ์ 
```

### ์ ์ฝ์กฐ๊ฑด ๋นํ์ฑํ

์ญ์  ์ FOREIGN KEY ์ ์ฝ์กฐ๊ฑด์ผ๋ก ์ปฌ๋ผ ์ญ์ ๊ฐ ๋ถ๊ฐ๋ฅํ ๊ฒฝ์ฐ ์ ์ฝ์กฐ๊ฑด์ ๋นํ์ฑํ ํ  ์ ์์

์์

```SQL
DELETE FROM DEPARTMENT
WHERE DEPT_ID = โD1โ;

ALTER TABLE EMPLOYEE
DISABLE CONSTRAINT EMP_DEPTCODE_FK CASCADE; -- ์ ์ฝ์กฐ๊ฑด ๋นํ์ฑํ

DELETE FROM DEPARTMENT
WHERE DEPT_ID = โD1โ;

ALTER TABLE EMPLOYEE
ENABLE CONSTRAINT EMP_DEPTCODE_FK; -- ์ ์ฝ์กฐ๊ฑด ํ์ฑํ
```

## โ๏ธ TRUNCATE

ํ์ด๋ธ ์ ์ฒด ํ ์ญ์  ์ ์ฌ์ฉํ๋ฉฐ DELETE๋ณด๋ค ์ํ ์๋๊ฐ ๋น ๋ฅด๊ณ  ROLLBACK์ ํตํด ๋ณต๊ตฌ ๋ถ๊ฐ๋ฅ  
๋ํ DELETE์ ๋ง์ฐฌ๊ฐ์ง๋ก FOREIGN KEY ์ ์ฝ์กฐ๊ฑด์ผ ๋๋ ์ ์ฉ ๋ถ๊ฐ๋ฅํ๊ธฐ ๋๋ฌธ์ ์ ์ฝ ์กฐ๊ฑด์ ๋นํ์ฑํ ํด์ผ ์ญ์ ํ  ์ ์์

```SQL
TRUNCATE TABLE EMP_SALARY;
SELECT * FROM EMP_SALARY;   -- ๋ชจ๋  ์ปฌ๋ผ์ด ์ญ์ ๋๊ธด ํ์ง๋ง ํ์ด๋ธ์ ๊ตฌ์กฐ๋ ๋จ์์์

ROLLBACK;   -- ROLLBACK ํ์๋ ์ปฌ๋ผ์ด ๋ณต๊ตฌ๋์ง ์์
```
