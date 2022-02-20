---
sort: 3
---

# SQL DML

<center> < **SQL DML (데이터 CRUD)** > </center>

- **Create(데이터 생성, 입력)**

    `INSERT INTO 테이블명 VALUES(값1, 값2);`: 테이블 **전체 컬럼에 대응하는 값을 모두 넣기.** 전체 레코드를 순서대로 입력.

    > 이때 문자열((VARCHAR))은 quotation mark(('))를 이용해야 한다.

    `INSERT INTO 테이블명 (컬럼1, 컬럼2) VALUES(값1, 값2);`: 테이블 **특정 컬럼에 대응하는 값만 넣기.**

    > 이때 지정되지 않은 컬럼은 디폴트 값 혹은 NULL 값이 들어감.

---

- **Read(데이터 읽기, 검색)**
    - 기본구조: **SELECT**

      `SELECT * FROM 테이블명;`: 테이블 **전체 컬럼의 데이터 모두 읽기.**
    
      > *: 전체라는 뜻.
    
      `SELECT 컬럼1, 컬럼2 FROM 테이블명;`: 테이블 **특정 컬럼의 데이터만 읽기.**
    
      `SELECT 컬럼1 AS 바꿀컬럼명, 컬럼2 AS 바꿀컬럼명 FROM 테이블명;`: 테이블 **특정 컬럼의 데이터를 검색**하되, 표시할 **컬럼명도 다르게** 하기.
    
      `ORDER BY 정렬기준컬럼명 DESC/ASC;`: 데이터를 **내림차순/오름차순** 정렬해서 읽기.
    
    - **조건문**
    
      `WHERE 컬렴명 >/=/< 값;`: **조건문에 맞는** 데이터만 검색.

      > 뒤에 `OR/AND`과 같 논리 연산자도 사용 가능.
    
      `WHERE 필드명 LIKE;`: **조건에 맞는** 데이터만 검색.
    
      > `LIKE '김%';`: '김'으로 시작하는 모든 값.
      >
      > `LIKE '%김%';`: '김'이 들어간 모든 값.
      >
      > `LIKE '김__';`: '김'으로 시작되고 뒤에 2글자가 붙는 값. 앞도 가능.
    
      `LIMIT 100, 10;`: 결과중 **100번째 다음부터,** **10개만** 가져오기.
    
      > `LIMIT 10;`: 결과중 처음부터 10개만 가져오기.
    

---

- **Read**_additional
  
    - **COUNT**
    
      `SELECT COUNT(*) FROM tb;`: **전체 row의 수** 반환.
    
      `SELECT COUNT(column) FROM tb;`: **특정 column의 row 수**를 반환.

      > 결측값은 count 되지 않음.

    - **통계**: SUM, AVG, MAX, MIN

      `SELECT SUM(column) FROM tb;`

      `SUM()`: column 값의 **합계**.

      `AVG()`: column 값의 **평균**.

      `MAX()`: **최대** column 값.

      `MIN()`: **최소** column 값.

    - **GROUP BY**

      `SELECT AVG(column) FROM tb GROUP BY gender;`: **그룹을 지어서**, 데이터를 분석.

      `GROUP BY`: WHERE 뒤에서 각 그룹별 통계 확인.

    - **HAVING**

      `SELECT column FROM tb GROUP BY column HAVING COUNT(*)>=100;`: **GROUP BY**의 column에 대한 **조건 비교**.

    - **DISTINCT**

      `SELECT DISTINCT cloumn FROM tb;`: **중복**된 column 값을 **출력하지 않음**.

    - **AS**

      `SELECT COUNT(*) AS abc FROM tb;`: **결과값의 이름 변경**.

      `tb a`: Table 이름 다음 한칸 띄고 새로운 이름을 쓰면, 구문 안에서 **AS와 유사**한 역할.

    - **INNER** **JOIN**

      `JOIN`: 두 개 이상의 Table로부터 필요한 데이터를 연결해 하나의 포괄적인 구조로 결합시키는 연산.

      `FROM tb1 INNER JOIN tb2 ON 매칭조건;`: Join하는 Table의 **ON 조건이 일치하는 결과만** 출력.

      매칭조건 예시: `tb1.COLUMN = tb2.COLUMN`

    - **OUTER JOIN**(참고)
    
      INNER JOIN과 달리 조건에 없는 값은 null로 다 붙임.
    
      LEFT나 RIGHT와 같이 쓰이며, 각 방향에 있는 테이블을 기준으로 함.
    
    - **SubQuery**
    
      `SubQuery`: SQL문 안에 포함된 (SQL)문. JOIN과 유사.
    
      `SELECT column FROM tb1 WHERE column 비교 (SELECT column FROM tb2 WHERE 조건);`: **tb1**의 column 값과 **tb2**의 column 값을 **비교**.
    
      > `비교`: `IN`, `>`, `<`, `=` 등.
    
      `SELECT column FROM (SELECT column FROM tb1);`: **다른 Table에서** **몇 개 값만** 가져오기.
    

---

- **Update(데이터 수정, 갱신)**

    조건문 없는 전체 데이터 수정은 실수로 판단하여 막고 있음. WHERE 조건문과 같이 쓰임.

    `UPDATE 테이블명 SET 기존컬럼명 = '수정컬럼명' WHERE 특정컬럼 >/=/< '값';`: 특정한 **조건에 맞는 데이터만 수정**.

    > 다수의 컬럼 값 수정 가능.

---

- **Delete(데이터 삭제)**

    `DELETE FROM 테이블명 WHERE 특정 컬럼 >/=/< '값';`: 특정한 **조건에 맞는 데이터만 삭제.**

    `DELETE FROM 테이블명;`: 테이블에 저장된 **모든 데이터 삭제.**