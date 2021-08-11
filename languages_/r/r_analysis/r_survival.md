---
sort: 3
---

# 생존분석

- [ ] **생존분석(Survival Analysis)**

- **Note**

    생존분석: 특정 events가 발생하기까지 기대시간 예측.

    events: 사망, 재발, 감염, 자살, 특종, 범죄, 재범, 이혼 등.

    - 생존분석 방법

      지수분포: 모수적 방법

      Kapaln-Meier model: 각 관측 시간마다 계산한 누적 계단 그림...

      > 비모수적 방법.

      Cox proportional hazald model

      > 준모수적 방법.

---

- **Kapaln-Meier model**

    `Surv(x, y)`: 데이터 준비. `x`중 조건 `y`의 이벤트가 발생한 경우.

    > +가 붙은 값은 censored
    >
    > `plot(with())`: 생존확률과 95% 신뢰구간을 그려줌.

    `survfit(Surv()~요인, data)`: Surv를 요인으로 구분해서 보여줌.

    > 해석: p-value가 낮으면 요인 별로 유의미. 그 요인이 중요하다.

---

- **Cox proportional hazald model**

    `coxph(Surv)`: 하나를 0 하나를 1로 두고, ~요인에 따라 선형회귀를 했다고 생각하면 됨.

    > 귀무가설: beta(coef) = 0. --- 유의확률로 검정.
    >
    > 해석: coef를 통해 기울기를 볼 수 있나?

    두 개의 모형(~sex+age)으로도 가능

    > 해석: 유의확률이 더 낮으면 더 중요한 요인이라는 것인 듯. 

    - 예측 기능

      `survfit(cox, newdata=)`: coxph() 모델에서 새로운 데이터를 줬을 때 event 생존 확률.

      > newdata: 만약 요인 a=1, b=200일 때에는?
      >
      > e.g. `,newdata=data.frame(sex=2, pat.karno=100))`

      `plot(survfit)`: 생존 확률 그래프.

      `survreg(Surv()	~요인, dist='weib, x)`: 데이터 x를 써서 요인별로 weibull 분포를 사용.

      > weibull: 모수적 방법, deafault임.

---

- **log-rank test**

    rank를 요인 별로 다른지 같은지를 보는 것.

    `survdiff(Surv)`: 카이제곱 p-value가 낮으면 성별로 차이가 있다.

    `predict(survreg, newdata=)`: 요인마다 weibull 분포를 따를 때의 기대 수명.