---
sort: 4
---

# 시계열 데이터

- [ ] **시계열 데이터(Time Series)**

- **시계열 데이터 만들기**

    `ts(data, start=)`: start부터 data를 시계열 데이터로 변환.

    > `,frequency=n)`: n번의 빈도, 분기처럼 내부를 나누는 것.

    `plot.ts(x)`: 시계열 데이터 만들기 똑같음.

---

- **시계열 분석**

    `decompose(ts)`: 시계열 데이터를 분해.

    `SMA(t1, n=이동평균수)`: 이동평균한 값을 생성.

    `auto.arima(data)`: 데이터를 활용해 최적의 ARIMA 모형 선택.

    `arima(data)`: 선정된 ARIMA 모형으로 데이터를 보정.
    
    > `, order=c(p,d,q))`
    >
    > 공식: X(t)-X(t-1) = 계수*e(t-1)
    
    `forecast(fitted, h=미래예측수)`: 미래의 값을 보정된 데이터로 예측.
    
    > `plot()`: 예측된 시계열 데이터

