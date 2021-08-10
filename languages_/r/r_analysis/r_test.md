---
sort: 1
---

# Test

- **One sample test**
    - **One sample t-test**

        전제: 모집단의 분포가 정규분포를 따른다.

        - t.test

        검정: `t.test(x, y=NULL, alternative=, mu=, conf.level=)`

        `x`: 벡터형 데이터

        `y`: 표본이 하나라 대조군이 없음.

        `alternative`: 판별 방향. — default 값은 양측 검정.
    
        > `'two.sided'` 양측, `'less'`, `'greater'`.
    
        `mu`: 모평균. — default 값은 0.
    
        `conf.level`: 신뢰수준. — 0~1.
    
        - 해석
    
        신뢰구간 안에 들어가면 귀무가설 채택.
    
        `alternative hypothesis`: 대립가설.
    
    - **Wilcoxon signed rank test**
    
        전제: 모집단의 분포가 정규분포를 따르지 않는다. 이상치가 있다.

        가정: 평균이 표본의 중앙값 근처이다.

        - wilcox.test

        검정: `wilcox.test(x,y=NULL, alternative=, mu=, conf.int=)`

        > `,correct=F)`: continuity correction을 안 하고 그냥 signed rank test 시행.
        >
        > 정규분포로 분산시키지 않고 이산확률분포로 알아서 보기.
    
        내용은 t-test와 같음.
    
        - 해석
    
        유의확률이 유의수준보다 낮으면 귀무가설 기각.
    
    - **정규성 검정**

        정규성 검정: 모집단이 정규분포를 따르는가.
        
        > 모수적 방법(t-test), 비모수적 방법(wilcoxon)
        
        - Shapiro Wilk Test
        
        Shapiro Wilk Test: 표본을 가지고 정규성 검정.
        
        귀무가설: 모집단이 정규분포와 같다.
        
        `shapiro.test(x)`: 벡터형 데이터인 표본 x의 정규성 검정.
        
        - qqnorm
        
        `qqnorm(x)`: x를 분위수 그래프로 표현.
        
        해석: y=x 직선 그래프의 근처에 있으면 정규분포다.
    

---

- **Two sample test**
    - **Two sample t-test**
        - t.test

        검정: `t.test(x, y, var.equal=F)`

        `var.equal`: 등분산 가정. — default 값은 `F`

        나머지: one sample t-test와 같음.

        참고로 y~x의 형식도 가능.

        - 해석

        유의확률이 유의수준보다 낮으면 귀무가설 기각.
        
        > == 서로 다르다.
        
    - **등분산 검정**
    
        검정: `var.test(x, y)`

        > F 분포 검정: 두 분산의 비.

        귀무가설: 두 모집단의 분산이 같다. F 값이 1이다.

        y~x의 형태도 가능.

    - **Wilcoxon test**
    
        검정: `wilcox.test(x, y)`
        
        y~x의 형태도 가능.
        
        귀무가설: 두 평균이 같다.
    

---

- **Paired sample test**

    대응 표본 검정: 동일 집단의 전후 비교.

    위의 test들에 `(,paired=T)`를 추가해주면 됨.

    귀무가설: 전과 후가 같다. 차이가 없다.

---

- **ANOVA**
    
    - **one-way ANOVA**
    
        `aov(y~x)`: y를 x로 분류하여 ANOVA 검정 시행.
    
        `anova(lm())`: 선형 모델에 ANOVA 검정 시행.
    
        > 효율적이라고는 하는데... ㅇㅅㅇ;;
        >
        > `aov()`와는 그저 문법 차이
    
        `summary()`: 분산분석표 확인 가능.
    
    - **기타**
    
        `oneway.test()`: 등분산이 아닌 경우 표본검정.

        `kruskal.test()`: 크루스칼-월리스 검정 시행.
    
        > ANOVA에 대비되는 비모수적 방법. --- 정규성X | 등분산X.

        `pairwise.t.test()`: 집단간 t-test 수행, 결과를 행렬로 반환.

        > 어느 두 집단이 차이가 나는지를 보여줌.
        >
        > `,pool.sd=T)`: 합동표본분산으로 계산. --- default:

        `bartlett.test()`: 각 세부 집단, 여러 집단의 등분산 검정.
    
    - **two-way ANOVA**
    
        `interaction.plot(x,z,y)`: 서론 간의 interaction을 확인.
    
        `friedman.test(y~x|z)`: y를 x와 z 별로 나누어서 검정.
        
        > 비모수적 방법: rank sum을 시행.

---

- **Regression**

    `lm(y~x)`: 선형회귀 모델

    > 해석: `intercept`가 y절편, `x`가 기울기/계수.
    >
    > 그림 그려줄 때는 저수준 그래픽스 `abline()`으로. + col

    `fitted()`: 데이터를 x로 받고 1차 직선 위 y 값을 각각 보여줌.

    `resid()`: fitted 값이 모델에 비해 실제 오차가 얼마인지 보여줌.

    `qqnorm(resid())`: 정규성검정

    `predict()`: fitted 값과 같은 값 반환.

    > `(,int='c')`: 95% 신뢰구간 예측.
    >
    > `(,int='p')`: prediction interval 예측. --- 에러도 표시됨.
    >
    > `(,newdata=)`: 데이터 x를 newdata로 받아가져와라.

    - **Regression analysis (다중회귀 분석)**

    분석대상: 독립변수가 2개 이상인 회귀모형

    `lm(y~x+z)`: 다중회귀 시행.

    `summary()`를 통해 유의확률을 살펴봄.

    > p-value가 큰 계수는 의미가 없다.
    >
    > 유의성과 설명력도 살펴보고...

    `anova(m1, m2)`: 유의확률이 크면 두 모델 비교에 큰 차이가 없다.

    `backward`: anova의 순서 변경, 유의확률 큰 변수 빼기 등의 과정.

---

- **Polynomial Regression**

    다항회귀: 제곱이나 상승이 들어감.

    > 식의 모양이 2차식이다...?

    `summary(with(data, lm(y~x+I(z^2))))`: x로 회귀

    > `I()`: 단지 하나의 항이라는 것을 알려주는 것.

    `predict(lm, interval=, newdata=)`: lm한 데이터를 95% 예측구간을 알 수 있음.

    유의수준 5% 하에서 차이가 있다...

---

- **Correlation**

    `cor()`: 데이터 간의 상관관계 구하기 --- NA가 있으면 에러.

    > `(,use='complete.obs)`: NA를 무시하고 구함.

    `cor.test()`: 상관관계 검정 --- 귀무가설: 관계가 없다.

    > `(,mothod='spearman')`: 비모수 검정.
    >
    > 모수 검정인 pearson이 default 값. kendall도 있음.

---

- **Logistic Regression**
    
    - **GLM**
    
        로지스틱 회귀: 선형회귀가 적합하지 않은 경우.

        > 0과 1로 이루어진 데이터.
    
        `glm(y~x+z, binomial)`: y를 x와z로 로지스틱 회귀분석 시행.

        > `,family=binomial('logit'))`: default 값.
        >
        > `,weights=)`: 분모가 무엇인지 알려준다.

        `summary(glm, corr=T)`: 분석 결과의 상관관계 확인.

    - **ANOVA**
    
        `anova(glm, test='Chisq')`: 유의확률이 크면 별 의미 없다.

        `drop1(glm, test='Chisq')`: 맨 끝에 놨을 때의 p-value를 보여준다.

        > 여기서 유의하지 않다고 나오면 없애도 된다.
        >
        > 모든 각각의 항목을 맨 밑에 와있을 때의 p-value를 보여주는데, 맨 끝에 있으면 앞에서 분류된 것에서 마지막 요인을 분류하는 것.
    
    - **Likelihood profiling**
    
        로지스틱 회귀에는 MSE와 같은 거리 개념이 잘 없다.
        
        > 그러면 뭐로 parameter를 조절?
        >
        > **likelihood profiling**: 어떤 data가 이럴 가능성이 가장 최대가 하는 parameter를 고르는 것.
        >
        > MLE
        
        confint와 exp함수...

---

- **Poisson Regression**

    포아송 회귀: 결과값이 비율인 경우 사용.
    
    > 종속변수가 포아송 분포를 따를 것으로 생각되는 경우
    
    `glm(y~x+z, offset=log(w), family=poisson)`
    
    > 포아송 분석에는 offset, poisson을 꼭 넣어줘야 함.
    >
    > 유의확률 값이 작으면 중요한 요인.
    
    `fitted(glm)`: x와 z에 따른 fitting.



- [ ] confint 신뢰구간.