---
sort: 4
---

# 문자열 숫자 변환

```note
원래 같은 문자열을 숫자로 바꾸려면 반복문을 이용했었는데, sklearn의 LabelEncoder를 이용하면 더 편하게 변환이 가능하다고 한다.
```

- **변환 전**

```python
li = ['남','녀','남','녀','녀']
df = pd.DataFrame(li, columns=['성별'])
df
```

|      | 성별 |
| :--: | :--: |
|  0   |  남  |
|  1   |  녀  |
|  2   |  남  |
|  3   |  녀  |
|  4   |  녀  |

- **변환 후**

```python
from sklearn.preprocessing import LabelEncoder
encoder = LabelEncoder()
encoder.fit(df['성별'])
labels = encoder.transform(df['성별'])
#print(labels)
df['성별'] = labels
df
```

|      | 성별 |
| :--: | :--: |
|  0   |  0   |
|  1   |  1   |
|  2   |  0   |
|  3   |  1   |
|  4   |  1   |
