---
sort: 1
---

# R 기초

- **출력**

    `print(“출력”)`: 한가지 자료형일 때 출력.

    `cat(“출”, 2*pi, "력”)`: 여러가지 자료형 포함 출력.

    `print(paste(“출”, 2*pi, ”력”))`: 여러가지 자료형 붙여서 출력.

    > `paste`: 나열된 원소 사이 공백을 두고 결과값 출력.

---

- **함수 정의**
  
    - **간단한 함수식**
    
      `함수명 ← function(x) 함수(x)`
    
    - **사용자 정의 함수**
    
      ```R
      함수명 ← function(매개변수) {
      	if (조건) return(결괏값)
      	else return(결괏값)
      }
      ```

---

- **파일 입출력**
  
    - **Rstudio directory**
    
        `getwd()`: 현재 디렉토리.
    
        `setwd()`: 디렉토리 설정.
    
    - **Library**
    
        `library()`: 패키지 불러오기.
    
        `ISwR::Stroke[1:10, 2:3]`: 패키지에서 데이터 바로 부르기.
    
    - **파일 읽기**
        - **txt 파일**
    
        `read.table(".txt")`: txt 파일 불러오기.
        
        > `,header=T`: header가 있음.
        >
        > `na.strings="값"`: 특정 값을 NA로 해석.
    
        - **csv 파일**
        
        `read.csv(".csv")`: csv 파일 불러오기.
        
        > `,header=FALSE`: 이 옵션이 없으면 항상 header가 있는 것으로 해석.
        
        - **파일 위치**
    
        디렉토리에 없으면 파일이름에 위치까지.
    
        > `\\`: 백슬래시를 2개로.
        
        홈페이지도 가능.
        
    - **파일 저장**
    
        `write.csv/table(데이터명, file="파일이름", row.names=FALSE)`: '데이터'를 '파일이름'으로 저장.
    
    - **데이터프레임 편집기**
    
        `fix()`: 데이터프레임을 편집기 열기. 데이터 변경O.
    
        `edit()`: 데이터프레임 편집기 열기. 데이터 변경X.

---

- **Data Handling**
  
    - **Bining(데이터 묶기**)
    
        `cut(x, y, labels= c())`: 벡터형 데이터를 구간에 따라 여러 집단으로 나누어 묶기.

        > `,include.lowest=T)`: NA가 생김.

        `quantile()`: 비슷한 개수의 그룹으로 나누기.

        `table()`: 테이블 형태로 보기 쉽게 만들어줌.

    - **벡터의 factor levels 정하기**
    
        `factor(x, labels=c())`: level을 설정하고 factor 설정.
    
        > labels는 level 0, a부터 이름 붙여줌.
    
        `levels() ← c()`: 벡터나 리스트로 지정한 이름들을 직접 level 값으로 지정.
    
    - **날짜 데이터로 변환**
    
        : 날짜는 서로 계산 가능
    
        `Sys.Date()`: 현재 날짜 알아내기.

        `as.Date("2020-11-28")`: 이 숫자를 Date 객체로 변환.
        
        > `(,format="%m/%d/%Y")`: 입력 문자열의 모습을 정의. (미국)
        
        `ISOdate(2020,2,29)`: "2020-02-29 12:00:00 GMT"
    
        > `as.Date()`: 해주면 년, 월, 일만 나옴.
        
        `as.POSIXlt()`: 날짜를 리스트로 표현.
        
        > `$mday`: month에서 몇번째 날인가.
        >
        > `$wday`: week에서 몇번째 요일인가. --- 1은 월요일.
        >
        > `$mon`: 1월으로투버 몇번째 달인가.
        >
        > `$year`: 1900년 이후 몇번째 년도인가.

---

- **ifelse**

    `ifelse(cond, T, F)`: 조건문 cond가 사실/거짓이면 T/F 출력.

---

- **기타**

`tolower()`: 소문자로 반환.

`transform(data, column=)`: data의 column 데이터 바꾸고 반환.