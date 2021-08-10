---
sort: 4
---

# 통계, 확률분포

- **통계량**

    `mean(x)`: 평균.

    `median(x)`: 중앙값.

    `sd(x)`: 표본표준편차.

    `var(x)`: 표본분산. (n-1)

    `cor(x)`: 상관계수.

    `cov(x)`: 공분산.

---

- **이산확률분포**

    - **이항분포**

      이항분포는 횟수가 많아지면 정규분포로 근사한다.

      `dbinom(x,size,prob)`: 이항분포의 확률밀도 함수/확률 값.

      > 1회 성공확률이 `prob`일 때, `size`번 중 `x`번 성공할 확률.
      >
      > ==`choose(size,x)*prob^{x}*(1-prob)^{size-x}`
      >
      > choose(x,y)`: x개 중 y개를 순서 상관 없이 뽑는 경우의 수.

      `pbinom(q,size,prob,lower.tail=T/F)`: 이항분포의 누적밀도 함수. ㄴ `lower.tail=T`: 아래에서 쭉 생각하는 것. 즉 `F`면 위에서부터니까 q번 초과로 성공활 확률.

      > : `size` 중 `q`번 이하로 성공할 확률.
      >
      > 이하 값을 다 더한 것임.

      `qbinom(p,size,prob,lower.tail=T/F)`: 이항분포의 분위수 함수.

      > : 누적 확률이 `p`보다 커지게 되는 성공횟수.

      `rbinom(n,size,prob)`: 이항분포의 난수생성함수.

      > : 성공확률이 `prob`인 `size`번의 시행에 대해 `n`번 랜덤 시행.

    - **포아송분포**

      ```
      E(X) = Var(X) = lambda
      ```

      `dpois(n,lambda)`: 사건이 평균 `n`번 발생할 확률.

      `ppois(n,lambda)`: 누적밀도함수로, 사건이 `n` 이하로 발생할 확률.

      > `lower.tail=F`: lambda 초과일 확률.

      `qpois(p,lambda)`: 확률이 `p` 이상일 때 사건 발생 수.

      `rpois(n,lambda)`: 랜덤하게 사건에서 `n`개 생성.

---

- **연속확률분포**
    - **균등분포**

        `dunif(x,min,max)`: 데이터 `x` 중 `구간 내`에서 균등분포를 가지는 값.

        `plot(x,dunif(x,min,max))`: 균등분포 그래프.

        `punif(q,min,max)`: `구간 내`의 균등분포 중 `min`부터 `q`까지의 확률.
    
        > 중간 확률: `punif - punif`.
    
        `runif(n,min,max)`: `구간 내`에서 균등분포를 따르는 난수 `n`개 생성.
    
    - **정규분포**
    
        `dnorm(x,mean,sd)`: `x`에 대해서 `평균`과 `표준편차`를 갖는  정규분포의 확률밀도함수.
    
        `pnorm(q)`: (표준)정규분포를 따를 때, -oo부터 `q`까지의 확률.
        
        > `pnorm(1.96) - pnorm(-1.96)` = 0.95
        
        `qnorm(p)`: 확률 p에 해당하는 구간.
    
        > `-무한~값`에 해당.
        
        `quantile(x, probs)`: 분위수 계산할 벡터 `x`를 가지고 확률을 설정하여 쓸 수 있음.

---

- **카이제곱분포**
    - **카이제곱분포**

        이하 x는 확률변수 값이다.

        `dchisq(x,df=)`:  카이제곱분포 확률밀도 값.

        `pchisq(x,df=)`: 누적 카이제곱분포.
    
        > 확률분포가 x 이하일 확률.
    
        `qchisq(x,df=)`: 분위수.

        > 누적 확률밀도함수가 x가 되는 값/지점.

        `rchisq(x,df=)`: 카이제곱 분포 랜덤 난수 생성.

        `lower.tail=F)`: x 초과 범위.

    - **그래프 그리기**
    
        `plot(x, dchisq(x,df=))`: 카이제곱분포 그래프 그리기.
        
        > `,dtype='l')`: 그래프 타입 지정.
        
        ``` R
        # 자유도에 따른 그림
        plot(x, dchisq(x, df=4), ylab='zkdlwprhq', type='l')
        points(x, dchisq(x, df=5), col='red', type='l')
        points(x, dchisq(x, df=10), col='blue', type='l')
        legend(15, 0.15, c('df=4','df=5','df=10'), lty=c('solid','solid','solid'), col=c('black','red','blue'))
        ```

---

- **t-분포**

    `dt(x, df=)`: t분포 확률밀도 값.

    `pt(x, df=)`: t분포 누적확률밀도분포.

    > X가 -oo부터 x까지일 확률.

    `qt(x, df=)`: 분위수.

    > -oo로부터 x 확률을 갖는 값. — 신뢰구간의 t0.975 값 구하기.

    `rt(x, df=)`: t분포 랜덤 난수 생성.

---

- **F-분포**

    `df(x, df=)`: F 분포 확률밀도 값.

---

- **Random Sampling**

    `sample(x,n)`: 범위 x 내의 n개의 난수 생성.