---
sort: 6
---

# Tabular Data

- **Table 만들기**

    `table()`: 테이블 형태의 데이터를 만듦. --- 열과 갯수로.

    `prop.table()`: 비율 표 만들기.

    `margin.table(t, n)`: 테이블을 행(n=1)이나 열(n=0) 별로 더함.

---

- **Single proprtions**

    `prop.test(n, N, p)`: N명 중 n명일 때 비율 p에 대한 검정.

    > 카이제곱 검정.

    `binom.test(n, N, p)`: 성공확률이 p인 베르누이 시행을 N번 할 때, n번 이하로 나올 확률을 다 더함.

---

- **Two independent proportion test**
    
    - lewitt and machin's example
    
      : X, Y개 중 각 x, y개 뽑히면 공정한가?
    
      귀무가설: 비율이 다르다고 할 수 없다.
    
      `prop.test(lewitt.machin.success, lewitt.machin.total)`

      > `,correct=F)`: continuity correction 없이 시행.
    
      `chisq.test(lewitt.machin)`: matrix 형태를 카이제곱 검정.

      > `prop.test()`와 똑같음.
      >
      > 여러가지를 분석할 때도 사용됨.
    
      `fisher.test(lewitt.machin)`: 카이제곱 검정과 유사. 
    
      > 가장 정확한 것은: Fisher's exact test.

---

- **K proportions(경향성 분석)**

    `prop.trend.test(a.yes, a.total)`: 경향성 검정.

    > 귀무가설: 경향성이 없다.

---

- **Power**

    Power: 귀무가설이 사실이 아닐때 귀무가설을 기각할 수 있는 힘.

    - **Power of one-sample and paried t-test**

        Non-central t-dstn
    
        > nu: noncentrality parameter
    
        `,type='paired')`: one-sample 페어인 경우.

        > `power.t.test(delta=, sd=, power=, type=)`

    - **Power of two-sample t-test**
    
        `power.t.test(delta=, sd=, sig.level=, power=)`
    
        > `delta`: 차이, true difference.
        >
        > `sd`: 표준편차.
        >
        > `sig.level`: 유의수준.
        >
        > `power`: 파워.

        `n=`를 설정하면 n 개수 검정 대신 power를 계산할 수 있음.
    
        `,alt='on.sided')`: 단측 검정
    
    - **Comparison of proportions**
    
        `power.prop.test(power=, p1=, p2=)`: 
        
        > power가 이럴 때, n을 이정도 뽑아야 한다.