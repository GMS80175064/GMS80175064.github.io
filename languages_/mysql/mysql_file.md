---
sort: 4
---

# 파일 실행 및 입력

- **SQL 파일 실행**
    
    - **Workbench**
    
      File > Open SQL Script > students.sql
    
    - **SQL terminal**
    
      `SOURCE C:\위치\students.sql;`: 같은 디렉토리에 없으면 위치 지정하여 불러옴.
    

---

- **Table에 데이터 한번에 입력**

    csv 파일 1행이 field로 들어감.

    - **Workbench**

      SCHEMAS > databases > Tables > table 우클릭 > Table Data Import Wizard > 파일 browse

    - **SQL terminal**

      `LOAD DATA INFILE`: 막혀있으니 있다는 것만 알아두셈.