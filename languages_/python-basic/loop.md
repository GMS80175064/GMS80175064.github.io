---
sort: 2
---

# Loop(제어문, 반복문)

- **Operators(조건문 연산자)**
    - **Comparison Operators(비교 연산자)**

        `a == b`: a와 b가 같다.

        `a != b`: a와 b가 같지 않다.

        `a >= b`: a가 b보다 크거나 같다.

    - **Logical Operators(논리 연산자)**

        `a or b`, `|`: a와 b 둘 중 하나만 참이어도 참이다.

        `a and b`, `&`: a와 b 모두 참이어야 참이다.

        `not a`: a가 거짓이면 참이다.

    - **Membership Operators(멤버 연산자)**

        `a in 리스트, 튜플, 문자열`: 리스트, 튜플, 문자열 안에 a가 있으면 참.

        `a not in 리스트, 튜플, 문자열`: 리스트, 튜플, 문자열 안에 a가 없으면 참.

    - **Assignment Operators(할당 연산자)**

        `a = 1`: 왼쪽 변수에 오른쪽 값을 할당.

        `+=`, `-=`, `*=`, `/=`, `%=`, `**=`, `//=`: 왼쪽 변수에서 오른쪽 값을 계산하고 왼쪽 변수에 할당.
        
        ㄴ ex) a += 2는 a = a+2와 같다.
        
        
    
- **If statement**

    `if 조건문:
        pass
    elif 조건문:
        수행할 문장1
    else:
        수행할 문장A`

    조건문이 참이면 if문 수행.

    조건문이 거짓이면 elif문 수행.

    elif 조건문이 거짓이면 else문 수행.

    `조건문`: 참과 거짓을 판단하는 문장.

    `pass`: 아무 수행 없이 넘어감.

    

- **While loop**

    `while 조건문:
        수행할 문장1
        수행할 문장2
        if 조건문:
            continue
        elif 조건문:
            수행할 문장A
            (break)`
    `else:` 

    조건문이 참인 동안 while문 아래 문장을 반복해서 수행.

    `continue`: 아래 코드는 무시하고 while문의 다음 회차를 진행함.

    `break`: while문을 빠져나감.

    `else`: 조건이 거짓일때 실행하고 while문 종료.
    ㄴ break로 반복이 끝나면 else절은 수행되지 않고 while문 종료.

    

- **For loop**

    `for 변수 in 리스트, 튜플, 문자열:
       수행할 문장1
        if 조건문:
            continue`
    `else:`

    ​	`for i in range(1, 11)
    ​	for (first, last) in [(1,2), (3,4)]
    ​	result = [num*3 for num in a if num%2==0]`

    리스트, 튜플, 문자열의 첫번째 요소부터 마지막 요소까지 차례로 변수에 대입되어 수행.

    `continue`: 아래 코드는 무시하고 for문의 다음 회차를 진행함.

    `for i, j in a, b` 형태도 가능

    `else`: 반복이 정상 종료된 직후 코드 실행.
    ㄴ break로 반복이 끝나면 else절은 수행되지 않고 for문 종료.

    iterrows, enumerate

`range(1, 11)`: 숫자 1부터 10까지의 숫자를 데이터로 갖는 객체.

`end=''`: 결괏값 print 시 줄을 넘기지 않고 한 줄에 계속 이어서 출력.

Indentation: 들여쓰기. colon(:)을 기준으로 들여써야 함.