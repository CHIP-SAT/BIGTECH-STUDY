# 데이터 정의 언어(DDL)

| 종류                                         | 설명                                     |
| -------------------------------------------- | ---------------------------------------- |
| **CREATE**                                   | 데이터베이스 혹은 데이터베이스 객체 생성 |
| **ALTER**                                    | 데이터베이스 객체 갱신                   |
| (예: 테이블에 필드 및 제약 조건을 추가/삭제) |
| **DROP**                                     | 데이터베이스 객체 삭제                   |
| (예: 테이블이나 데이터베이스를 삭제)         |
| **TRUNCATE**                                 | 테이블 구조를 유지한 채 모든 레코드 삭제 |

## CREATE

### 데이터베이스 생성

```sql
CREATE DATABASE mydb;

CREATE TABLE users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    birthdate DATE,
    registration_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

- AUTO_INCREMENT → 자동 증가
- DEFAULT → 기본값 설정
- NOT NULL → 필수값
- UNIQUE → 중복 금지

<aside>
⭐

특정 필드가 지켜야 할 제약 조건

| 키워드             | 제약 조건                                    |
| ------------------ | -------------------------------------------- |
| **PRIMARY KEY**    | 특정 필드를 기본 키로 지정 (중복 X + NULL X) |
| **UNIQUE**         | 특정 필드가 고유한 값을 갖도록 설정 (중복 X) |
| **FOREIGN KEY**    | 특정 필드를 외래 키로 지정                   |
| **DEFAULT 기본값** | 기본값 지정                                  |
| **NULL/NOT NULL**  | 특정 필드에 NULL 값을 허용/허용하지 않음     |

</aside>

---

## ALTER

### 테이블 구조 변경

```sql
-- 새로운 필드 추가
-- ALTER TABLE 테이블_이름 ADD COLUMN 필드_이름 필드_타입 [제약 조건]
ALTER TABLE posts ADD COLUMN new_field VARCHAR(50) NOT NULL;

-- 기존 필드 수정
-- ALTER TABLE 테이블_이름 CHANGE COLUMN 기존_필드_이름 새_필드_이름 필드_타입 [제약 조건]
ALTER TABLE posts CHANGE COLUMN new_field old_field VARCHAR(30) NOT NULL;

-- 기존 필드 삭제
-- ALTER TABLE 테이블_이름 DROP COLUMN 필드_이름
ALTER TABLE posts DROP COLUMN old_field;

-- 외래 키 제약 조건 추가
-- ALTER TABLE 테이블_이름 [ADD CONSTRAINT 제약_조건_이름]
-- ADD FOREIGN KEY (필드_이름) REFERENCES 참조_테이블_이름(참조_필드)
ALTER TABLE posts ADD FOREIGN KEY (user_id) REFERENCES users(user_id);

-- UNIQUE 제약 조건 추가
-- ALTER TABLE 테이블_이름 [ADD CONSTRAINT 제약_조건_이름] UNIQUE (필드_이름)
ALTER TABLE posts ADD UNIQUE (title);

-- NOT NULL 제약 조건 추가
-- ALTER TABLE 테이블_이름 MODIFY 필드_이름 필드_타입 NOT NULL
ALTER TABLE users MODIFY email VARCHAR(100) NOT NULL;

-- 기본 키 설정 (PRIMARY KEY로 사용 중인 필드가 없을 경우)
-- ALTER TABLE 테이블_이름 ADD PRIMARY KEY (필드_이름)
ALTER TABLE posts ADD PRIMARY KEY (post_id);
```

---

## DROP

### 테이블 삭제

```sql
DROP DATABASE 데이터베이스_이름;
DROP TABLE 테이블_이름;
```

---

## TRUNCATE

### 테이블의 구조를 유지한 채로 테이블의 모든 레코드 삭제

```sql
TRUNCATE TABLE 테이블_이름;
```

<aside>
🗣

**DROP vs TRUNCATE**

| 구분     | 설명               |
| -------- | ------------------ |
| DROP     | 테이블 자체 삭제   |
| TRUNCATE | 데이터만 전체 삭제 |

</aside>

---

# 데이터 조작 언어(DML)

| 종류   | 설명                 |
| ------ | -------------------- |
| SELECT | 테이블의 레코드 조회 |
| INSERT | 테이블에 레코드 삽입 |
| UPDATE | 테이블의 레코드 수정 |
| DELETE | 테이블의 레코드 삭제 |

## INSERT

### 레코드 삽입

```sql
INSERT INTO 테이블_이름(필드1, 필드2) VALUES (값1, 값2);

-- 여러 레코드를 한 번에 삽입하는 경우
INSERT INTO 테이블_이름(필드1, 필드2, 필드3) VALUES
	(값1, 값2, 값3),
	(값1, 값2, 값3),
	(값1, 값2, 값3);
	...
	;
```

- 기본값 : NULL

<aside>
⚠️

무결성 제약 조건에 위배된 레코드 삽입

```sql
-- NOT NULL 제약 조건 위배: username은 NULL이 될 수 없기 때문에 실행되지 않음
INSERT INTO users (username, email) VALUES (NULL, 'no_name@example.com');

-- UNIQUE 제약 조건 위배: kim@example.com이 이미 존재할 경우 실행되지 않음
INSERT INTO users (username, email) VALUES ('kim', 'kim@example.com');

-- 외래 키 제약 조건 위배: users 테이블에 user_id가 10인 레코드가 존재하지 않을 경우 실행되지 않음
INSERT INTO posts (user_id, title, content) VALUES (10, 'Hi', 'Hello');
```

</aside>

---

## UPDATE

### 레코드를 수정

```sql
UPDATE 테이블_이름
	SET 필드1 = 값1, 필드2 = 값2, ...
	-- '='는 비교 연산자
	WHERE 조건식;
```

| 연산자              | 설명                                             |
| ------------------- | ------------------------------------------------ |
| =                   | 같을 경우 참                                     |
| >                   | 클 경우 참                                       |
| <                   | 작을 경우 참                                     |
| >=                  | 크거나 같을 경우 참                              |
| <=                  | 작거나 같을 경우 참                              |
| <>                  | 다를 경우 참                                     |
| 조건식1 AND 조건식2 | 조건식1과 조건식2가 모두 만족할 경우 참          |
| 조건식1 OR 조건식2  | 조건식1과 조건식2 둘 중 하나만 만족할 경우 참    |
| NOT 조건식          | 조건식이 아닐 경우 참                            |
| IN                  | IN 뒤에 명시되는 값과 하나 이상이 일치할 경우 참 |

---

## DELETE

### 레코드를 삭제

```sql
DELETE 테이블_이름
	WHERE 조건식;
```

<aside>
⭐

외래 키 제약 조건 - ON UPDATE, ON DELETE [그림]

| 제약 조건   | 설명                                            |
| ----------- | ----------------------------------------------- |
| CASCADE     | 참조하는 데이터도 함께 수정/삭제함              |
| SET NULL    | 참조하는 데이터를 NULL로 변경함                 |
| SET DEFAULT | 참조하는 데이터를 기본값(default)으로 변경함    |
| RESTRICT    | 수정/삭제를 허용하지 않음                       |
| NO ACTION   | (MySQL의 경우)사실상 RESTRICT와 동일하게 동작함 |

</aside>

---

## ⭐ SELECT

### 삽입된 레코드를 조회

```sql
SELECT 필드1, 필드2, ...
	FROM 테이블_이름
	WHERE 조건식
	GROUP BY 그룹화할_필드
	HAVING 필터_조건
	ORDER BY 정렬할_필드
	LIMIT 레코드_제한
```

- - : 모든 필드드

<aside>
📎

패턴 검색과 연산/집계 함수

LIKE 연산자

와일드카드 문자(%,\_)

% : 0개 이상의 임의의 문자와 일치한다

\_ : 정확히 1개인 임의의 문자와 일치

```sql
SELECT first_name, last_name, major
	FROM students
	WHERE major = 'Computer Science';
```

- LIKE 연산자 사용

```sql
SELECT first_name, last_name, major
	FROM students
	WHERE major LIKE '%Science%';
```

- 두 번째 문자가 ‘a’인 모든 학생을 반환

```sql
SELECT first_name, last_name, major
	FROM students
	WHERE major LIKE '_a%';
```

- 연산/집계 함수는 조회된 레코드에 대한 특정 연산을 수행하거나 집계하는 함수

| 함수  | 설명                            |
| ----- | ------------------------------- |
| COUNT | 조회된 레코드 개수를 반환함     |
| SUM   | 조회된 레코드의 총합을 반환함   |
| AVG   | 조회된 레코드의 평균을 반환함   |
| MAX   | 조회된 레코드의 최댓값을 반환함 |
| MIN   | 조회된 레코드의 최솟값을 반환함 |

- ‘students’ 테이블의 레코드 수(학생 수)와 평균 학점, 최고 학점, 최저 학점을 조회

```sql
SELECT COUNT(*), AVG(gpa), MAX(gpa), MIN(gpa) FROM students;
```

</aside>

### GROUP BY

#### 특정 필드를 기준으로 필드를 그룹화

```sql
SELECT major, COUNT(*) AS student_count
	FROM students
	GROUP BY major;
```

![image.png](attachment:b8ba6467-e080-4e98-9c27-db1d1fbd3e2a:image.png)

---

### HAVING

#### GROUP BY절로 그룹화된 결과에 조건을 적용

- WHERE절에 명시되는 조건식이 ‘그룹화되기 전 개별 레코드’
- 명시되는 조건식은 ‘그룹화된 레코드’에 대한 조건식

```sql
SELECT major, AVG(gpa)
	FROM students
	GROUP BY major
	HAVING AVG(gpa) >= 3.6;
```

![major 필드를 기준으로 그룹화한 gpa 필드의 평균을 구하는 테이블 (HAVING 전)](attachment:356624b0-aed8-4181-9860-50e28c55eed8:image.png)

major 필드를 기준으로 그룹화한 gpa 필드의 평균을 구하는 테이블 (HAVING 전)

![평균 GPA가 3.6이상인 레코드가 조회된 테이블 (HAVING 후)](attachment:79fcd62c-69ef-440e-bcad-48f2a9f4e9f6:image.png)

평균 GPA가 3.6이상인 레코드가 조회된 테이블 (HAVING 후)

---

### ORDERY BY

#### 특정 필드를 기준으로 데이터를 정렬

**오름차순(ASC) | 내림차순(DESC)**

```sql
SELECT first_name, last_name, gpa
	FROM students
	ORDER BY gpa DESC;

SELECT first_name, last_name, major
	FROM students
	ORDER BY last_name ASC;

SELECT first_name, last_name, enrollment_date
	FROM students
	ORDER BY enrollment_date ASC;
```

---

### LIMIT

#### 조회할 레코드 수를 제한

![상위 3개의 레코드만 조회된 테이블](attachment:d1ca14bb-3b64-4620-9ff4-027589818e2c:image.png)

상위 3개의 레코드만 조회된 테이블

![LIMIT(2,2)는 두 번째로 떨어진 레코드로부터 2개의 레코드를 조회하는 테이블](attachment:7d60a518-569b-44be-a58b-3991c3427e75:image.png)

LIMIT(2,2)는 두 번째로 떨어진 레코드로부터 2개의 레코드를 조회하는 테이블

<aside>
❗

SELECT문은 순차적으로 수행X 다음과 같이 수행O

**FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT**

</aside>

---

# 트랜잭션 제어 언어(TCL)

| 종류      | 설명                      |
| --------- | ------------------------- |
| COMMIT    | 데이터베이스에 작업 반영  |
| ROLLBACK  | 작업 이전의 상태로 되돌림 |
| SAVEPOINT | 롤백의 기준점 설정        |

```sql
START TRANSACTION;

UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;

COMMIT;
```

### 실패시

```sql
ROLLBACK;
```

- 전체 작업 취소

---

## SAVEPOINT

### 특정 시점으로 되돌림

```sql
SAVEPOINT 세이프포인트_이름
ROLLBACK TO SAVEPOINT 세이프포인트_이름
```

<aside>
📎

#### 자동 커밋 (MySQL 특징)

MySQL은 기본적으로 **자동 COMMIT**

```sql
SET autocommit=0;
```

- 자동 커밋 끄기
</aside>

---

# 데이터 제어 언어(DCL(Data Control Language))

| 종류   | 설명                   |
| ------ | ---------------------- |
| GRANT  | 사용자에게 권한 부여   |
| REVOKE | 사용자로부터 권한 회수 |
