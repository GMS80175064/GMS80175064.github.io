---
sort: 2
---

# SQL DDL

- [ ] **SQL DDL (Schema 정의)**

- **Database**

    `CREATE DATABASE dbname;`: dbname이라는 이름의 **데이터베이스 생성**.

    - **기본키 셋**

        `DEFAULT CHARSET=UTF8`:  한글 데이터 처리.
        
        > CHARACTER SET: 문자가 컴퓨터에 저장될 때 어떠한 코드로 저장될지에 대한 규칙의 집합.
        
        `COLLATE=UTF8`: 비교, 검색, 정렬 시 유니코드 기반으로 하라는 뜻.

    `SHOW DATABASES;`: 존재하는 **모든 데이터베이스들**을 보여줌.

    `DROP DATABASE dbname;`: dbname **데이터베이스 삭제**.

    `DROP DATABASE **IF EXIST** dbname;`: 혹여나 dbname 데이터베이스가 있으면 삭제하고, **없으면 에러를 내지 말고** 다른 명령을 실행해라.

    `USE dbname;`: 앞으로는 dbname **데이터베이스를 사용**할 것을 선언.

---

- **Table**

    ```mysql
    # tb라는 이름의 **테이블**을, 아래의 기본키 셋으로 **생성**.
    CREATE TABLE tb (
    	컬럼명 데이터형 옵션
    	컬럼명 데이터형
    	PRIMARY KEY(컬럼명)
    	FOREIGN KEY (컬럼명2) REFERENCES tb2(컬러명2)
    );
    ```

    - **기본키 셋**

        컬럼명: 영어 소문자 중심.

        - 데이터형(type)

        `INT, FLOAT, TEXT(), VARCHAR() 등`

        - 옵션

        `UNSIGNED:` 양수.

        `NOT NULL:` Null 값 없이.

        `AUTO_INCREMENT:` 자동 채우기.

        `ENUM('a', 'b')`: a와 b 값 중 하나만 가질 수 있음.

        `DEFAULT CHARSET=UTF8`: 문자를 어떤 코드로 저장할지.

        > `CREATE()` 밖에서 선언.

        `PRIMARY KEY`: 키셋으로 primary key 지정 가능.

        > 컬럼명 정의하면서 옵션으로 넣어줄 수도 있음.

    - **Foreign Key**

        데이터 무결성: 두 테이블간 관계에 있어서, 데이터의 정확성을 보장하는 제약 조건.

        `FOREIGN KEY (컬럼명) REFERENCES tb2(컬럼명)`: t1 테이블 생성 시 작성.

        - **INSERT**

          참조하는 `tb2` 테이블에 데이터가 없으면 INSERT가 안됨. 즉 `tb2`에 a라는 데이터가 없으면 `tb1`에도 a는 작성이 되지 않고오류가 뜸.

          만약 꼭 a 데이터를 INSERT 하고 싶으면, `tb2`에 먼저 a 데이터를 INSERT 하고 나서 `tb1`에서 참조하여 넣을 수 있음.

        - **DELETE**

          `tb1`에서 참조하고 있는 `tb2`의 데이터를 삭제하려고 해도 오류.

    - **명령**

        `SHOW tables;`: 데이터베이스 내의 **모든 테이블 확인.**

        `DROP TABLE tb;`: tb **테이블 삭제**.

        `DESC tb;`: tb **테이블의 구조**를 보여줌.

        `ALTER TABLE 테이블명 ADD COLUMN 컬럼명 데이터형 옵션;`: 테이블에 위의 기본키 셋을 가진 **컬럼 추가**.

        `ALTER TABLE 테이블명 MODIFY COLUMN 컬럼명 데이터형 옵션;`: 테이블 내 **컬럼의 데이터형을 변경**.

        `ALTER TABLE 테이블명 CHANGE COLUMN 기존컬럼명 바꿀컬럼명 (데이터형 옵션);`: 테이블 내 **컬럼의 이름을 변경**. 여기서 데	이터형도 바꿀 수 있다.

        `ALTER TABLE 테이블명 DROP COLUMN 컬럼명;`: 테이블 내 **컬럼을 삭제**.