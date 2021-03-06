---
sort: 3
---

# Input/Output(파일 입출력)

- **Input/Output(사용자 입력과 출력)**

    `input("내용")`: "내용"을 사용자에게 보여주고 입력을 받음. **문자열로** 취급.

    `int(input("내용"))`: 숫자형으로 취급.

    문자열 띄어쓰기: comma를 사용하면 문자열 사이에 띄어쓰기 가능. quotation mark로 둘러싸인 문자열은 '+' 연산과 동일하게 붙여짐.

    - input 반복

    'while 변수 조건'의 마지막에 `변수 = input("내용")` 다시 실행.

    한줄로는 `while input("내용") == "abc"`

---

- **File handling(파일 다루기)**
    - **Basic: handling**

        `파일 객체 = open(파일명, 열기 모드)`: '파일 이름'과 '파일 열기 모드'를 입력값으로 받고, 결괏값으로 파일 객체를 돌려준다.

        `파일명`: `'새파일.txt'`의 형태.

        `파일 위치`: `'C:\파일위치\새파일.txt'`처럼 위치도 지정 가능.

        > `/`나 `\\`로 작성해야 하는 경우도 있음.

        `열기 모드`: `'r'`은 읽기만 하는 읽기모드, `'w'`는 새로 쓰는 쓰기모드, `'a'`는 마지막에 추가하는 추가모드.

        `encoding='UTF-8'`: 한글 문서일 때.

        `f.close()`: 열려 있는 파일 객체 f를 직접 닫아줌.

        `next(f)`: 첫번째 줄을 날리거나, 별도 보관.

    - **Create(파일 생성)**

        `f = open('새파일.txt', 'w')`: 파일을 현재 디렉터리 혹은 지정 위치에 생성하고, 파일 객체 f를 돌려준다.

        `'w'`: 파일이 이미 존재하면 기존의 내용 모두 삭제, 존재하지 않으면 새로운 파일 생성.

    - **Write(파일 새로 쓰기)**

        `f = open('C:\파일 위치\이름', 'w')`: 지정 위치의 파일을 기존 내용 삭제 후 쓰기 모드로 열기.

        `f.write(내용)`: 파일에 출력값인 (내용)을 직접 작성.

    - **Read(파일 읽기)**

        `f = open('C:\파일 위치\이름', 'r')`: 지정 위치의 파일을 읽기 모드로 열기.

        `f.readline()`: 파일의 첫번째 줄을 읽어 line 객체로 돌려줌. 읽을 줄이 없으면 빈 문자열을 돌려줌.

        `f.readlines()`: 파일의 모든 줄을 읽어 lines 객체에 리스트로 돌려줌.

        `f.read()`: 파일의 내용 전체를 data 객체에 문자열 하나로 돌려줌.

        - 참고: 모든 줄 출력

        ```python
        while True:
            line = f.readline()
            if not line: break
           	print(line)
        lines = f.readlines()
        for line in lines:
            print(line)
        ```

    - **Append(파일 내용 추가)**

      `f = open('C:\파일 위치\이름', 'a')`: 지정 위치의 파일을 추가모드로 열기

      `f.write(내용)`: 'r'모드에서는, 파일에 출력값인 (내용)을 마지막 내용 다음부터 작성.

    - **With 문**

        ```python
        with open(파일명, 열기모드) as f:
           f.write(내용)
        ```

        : with 블록을 벗어나는 순간 열린 파일 객체 f가 자동으로 close 됨.

    - **csv 파일**

        import csv를 이용.

        `csv.reader(f)`: r모드로 열고, csv 객체 반환.

        `csv.writer(f)`: w모드로 열고, csv 객체 반환.

        > `wr.writerow(row)`: 파일에 행을 추가하기 위해 row 리스트를 넘겨줌.

    ---

    읽고 쓰는 내용은 문자열.

    `UTF-8`: 모든 언어를 0과 1로 처리해주는 유니코드 중에 가장 많이 쓰이는 코드.

    > 그 외: cp949(euc-kr) 등
    >
    > `'w'` 모드로 파일을 불러오면 내용이 삭제됨을 인지할 것.