---
sort: 3
---

# 연산

- **기초 수학**

    vector형 변수의 같은 위치끼리 연산, 함수 적용 가능.

    - **기본 계산**

        사칙연산과 제곱: Python과 같음.

        `x%%y`: x를 y로 나눈 나머지.

        `x%/%y`: x를 y로 나눈 정수 몫.

        `x%*%y`: 행렬곱셈.

        `x%in%y`: x가 y면 True, 아니면 False 반환.

        `!`: 논리부정(!=)

    - **수학 관련 함수**

        `sqrt()`: 루트.

        `factorial(n)`: n!

        `floor(x)`: x 이하 최대 정수.

        `ceiling(x)`: x 이상 최소 정수.

        `trunc(x)`: x 소수점 버림.

        `round(x, y)`: x를 소수점 y째까지 반올림.

        `signif(x, y)`: x를 정수 y째까지 반올림.

        `gcd(x, y)`: x, y의 최대공약수.


---

- **기타 연산**

    `length()`: 자료 길이.

    `rnorm(30)`: 표준정규분포에서 난수 30개 생성.

    `seq(1, 30)`: 1부터 30까지의 정수 생성. (=`1:30`)
    
    > `,lengh.out=5)`: 간격을 5로 나눈 등차수열.
    >
    > `,by=2`): 간격 2단위(홀짝).

    `rep(x, times=y)`: x를 y번 반복.
    
    `choose(n, y)`: 서로다른 n개에서 y개를 선택하는 조합의 수.
    
    > == nCy
    
    - 참고
    
    `asin()`: arcsin 함수.
    
    `exp(n)`: e^n 자연로그.

    `log2(n)`: 밑이 2인 로그함수. 밑이 없으면 자연상수 e가 밑.
    
    > == `log(n, 2)`
    
    `complex(real=0, imaginary=1)`: 0+1i인 복소수.