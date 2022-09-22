# DDL

데이터 정의 언어로 객체(OBJECT)를 만들고(CREATE), 수정하고(ALTER), 삭제(DROP)하는 구문을 말함

오라클 객체 종류  
 테이블(TABLE), 뷰(VIEW), 시퀀스(SEQUENCE), 인덱스(INDEX),
패키지(PACKAGE), 프로시저(PROCEDUAL), 함수(FUNCTION),
트리거(TRIGGER), 동의어(SYNONYM), 사용자(USER)

## CREATE

테이블이나 인덱스, 뷰 등 데이터베이스 객체를 생성하는 구문

### 표현식

CREATE TABLE 테이블명(  
 컬럼명 자료형(크기),  
 컬럼명 자료형(크기),  
 …  
 );

```SQL
CREATE TABLE MEMBER(
  ID VARCHAR2(20),
  NAME VARCAHR2(10),
  PHONE VARCHAR2(20)
);
```

오라클 자료형
![오라클 자료형](https://user-images.githubusercontent.com/105089699/188309380-ebcd1d8e-9921-48ac-ae93-bb122d7c7f94.png)

### 컬럼 주석

테이블의 컬럼에 주석을 다는 구문

표현식  
COMMENT ON COLUMN 테이블명.컬럼명 IS '주석 내용';

```SQL
COMMENT ON COLUMN MEMBER.ID IS '아이디';
COMMENT ON COLUMN MEMBER.NAME IS '이름';
COMMENT ON COLUMN MEMBER.PHONE IS '전화번호';
```

### 제약 조건

테이블 작성 시 각 컬럼에 기록될 데이터에 대해
제약 조건을 설정할 수 있는데 이는 데이터 무결성 보장을 주 목적으로 함  
입력 데이터에 문제가 없는지에 대한 검사와
데이터 수정/삭제 가능 여부 검사 등을 위해 사용

`데이터 무결성 : 데이터의 정확성, 유효성, 일관성이 유지되는 것`

![제약조건](https://user-images.githubusercontent.com/105089699/188381955-f4d114a4-1dc6-49b6-a187-a464362191d3.png)

- NOT NULL  
  해당 컬럼에 반드시 값이 기록되어야 하는 경우 사용  
  특정 컬럼에 값을 저장/수정할 때는 NULL값을 허용하지 않도록 컬럼 레벨에서 제한

```SQL
CREATE TABLE USER(
  USER_ID VARCHAR2(20) ,
  USER_PWD VARCHAR2(20) NOT NULL,
  USER_NAME VARCHAR2(20) NOT NULL,
  EMAIL VARCHAR2(30),
  PHONE VARCHAR2(20)
);
```

- UNIQUE  
  컬럼 입력 값에 대해 중복을 제한하는 제약조건으로  
  컬럼 레벨과 테이블 레벨에 설정 가능

```SQL
CREATE TABLE USER(
  USER_ID VARCHAR2(20) ,
  USER_PWD VARCHAR2(20) NOT NULL,
  USER_NAME VARCHAR2(20) NOT NULL,
  EMAIL VARCHAR2(30) UNIQUE, -- 컬럼 레벨 제약조건 설정
  PHONE VARCHAR2(20),
  UNIQUE(PHONE) -- 테이블 레벨 제약조건 설정
);
```

- PRIMARY KEY  
  테이블에서 한 행의 정보를 구분하기 위한 고유 식별자 역할  
  NOT NULL의 의미와 UNIQUE의 의미를 둘 다 가지고 있으며
  한 테이블 당 하나만 설정 가능  
  컬럼 레벨과 테이블 레벨 둘 다 지정 가능

```SQL
CREATE TABLE USER(
  USER_ID VARCHAR2(20) PRIMARY KEY,
  USER_PWD VARCHAR2(20) NOT NULL,
  USER_NAME VARCHAR2(20) NOT NULL,
  EMAIL VARCHAR2(30) UNIQUE, -- 컬럼 레벨 제약조건 설정
  PHONE VARCHAR2(20),
  UNIQUE(PHONE) -- 테이블 레벨 제약조건 설정
);
```

`제약조건 확인 : DESC 테이블명;`
