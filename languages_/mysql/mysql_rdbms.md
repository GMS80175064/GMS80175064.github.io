---
sort: 1
---

# RDBMS

- **RDBMS & Schema**

    `DBMS`: 데이터베이스를 관리하는 시스템.

    `RDBMS`: 관계형 데이터베이스 관리 시스템. (테이블!)

    `Table`: 엑셀의 sheet와 유사한 개념.

    `Column = Field`: **열**

    `Row = Record`: **행**

    `Primary Key`: 각 레코드를 **유일하게 식별**해주는 필드로, **Null 없이 유일**한 값이어야 함.

    **`Schema`**: 데이터 저장을 위해 처음 해야할 일이자 데이터를 저장하기 위한 설계도. 테이블, 각각의 테이블에 어떤 필드가 들어갈지, 테이블 간의 관계를 어떻게 맺어야할지를 정리.

---

- **SQL과 세 가지 종류**

    `SQL`: 데이터베이스가 스키마를 위해 제공하는 명령들, 즉 SQL 언어를 이용하여 Schema가 테이블을 정의.

    **`DDL(데이터 정의 언어)`**: **테이블, 스키마를 정의**할 수 있는  언어, 기능.

    **`DML(데이터 조작 언어)`**: **데이터 CRUD**(생성, 읽기, 갱신, 삭제).

    `DCL(데이터 제어 언어)`: 데이터 권한 제공, 무결성 검정 등 전문가의 영역.



- Semi colon(;)을 마지막에 쓰지 않으면 여러 줄을 작성 중인 하나의 명령으로 이해하고 실행 안 함.



