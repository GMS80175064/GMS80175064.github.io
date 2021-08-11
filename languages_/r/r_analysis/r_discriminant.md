---
sort: 2
---

# 판별분석

cross entropy: `-tlogP0-(1-t)log(1-P0)`

- **library(caret)**

    `featurePlot(x=, y=, plot='ellipse')`: x라는 feature와 y라는 label로 plot을 ellipse로 각각 묶어줘라.

    > 데이터가 생긴 모양을 보기 위해.


---

- **학습용 데이터 만들기**

    `createDataPartition(d, p=, list=)`: p:1-p 비율로 데이터를 나눠줌.

    `d[-code,]`: code를 제외한 값을 보여줌.

---

`train(Species~., data=, method=, metric=, trControl=)`: Species를 나머지를 다 사용해서 찾아내라.

> `method`: 'lda', 'rpart', 'knn', 'svmRadial', 'rf'

`resamples(list(lda=, cart=, knn=, svm=, rf=)`: 리스트로 만들어 묶은 것.

`predict()`: 모델을 가지고 prediction 하는 것.

`confusionMatrix()`: prediction 한 것과 실제 데이터를 비교하는 것.