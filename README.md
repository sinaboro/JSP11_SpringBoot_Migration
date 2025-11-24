# JSP11_SpringBoot_Migration

## 1. 데이터베이스 및 계정 생성

```sql
-- 데이터베이스 생성
CREATE DATABASE edudb;

-- 계정 생성
CREATE USER 'jdbctest'@'%' IDENTIFIED BY 'jdbctest';

-- 권한 부여
GRANT ALL ON edudb.* TO 'jdbctest'@'%';

-- 권한 적용
FLUSH PRIVILEGES;


## 2. 데이터베이스 선택
'''
USE edudb;
'''


## 3. 데이블 생성
CREATE TABLE board (
    num       INT PRIMARY KEY AUTO_INCREMENT,
    pass      VARCHAR(30)  NOT NULL,
    name      VARCHAR(30),
    email     VARCHAR(30),
    title     VARCHAR(50),
    content   VARCHAR(1000),
    readcount INT          DEFAULT 0,
    writedate DATETIME     DEFAULT CURRENT_TIMESTAMP
);


### 데이블 컬럼 정보 확인
desc board;

### 데이블 데이타 입력
INSERT INTO board(name, email, pass, title, content)
VALUES('성윤정', 'pinksung@nate.com', '1234', '첫방문', '반갑습니다.');
INSERT INTO board( name, email, pass, title, content)
VALUES('성윤정', 'pinksung@nate.com', '1234', '김밥', '맛있어요.');
INSERT INTO board( name, email, pass, title, content)
VALUES('전수빈', 'raccon@nate.com', '3333', '고등애', '일식입니다.');
INSERT INTO board( name, email, pass, title, content)
VALUES('전원지', 'one@nate.com', '1111', '갯골마을', '돼지삼겹살이 맛있습니다.');
commit;

select * from board;
