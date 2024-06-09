## 다중 선형회귀

![image](https://github.com/eileenjang/statistics/assets/82510378/46879df1-a65f-4182-a42b-75e6a926eeee)

상관계수 (correlaction coefficient)는 두 변수 간 선형관계를 나타내는 척도이기 때문에 단순 선형회귀에서만 쓰인다.
또한 다중 선형회귀식에서는 양적 데이터뿐만 아니라 범주형 데이터를 사용하는 방법도 알아볼 것이다.
회귀 모형에 포함되는 예측변수 선정기준은 아래와 같다.
- 종속변수와 높은 상관관계
- 예측변수와 낮은 상관관계 (다중공선성 문제)
- 예측변수 개수는 적을수록 유리

### 변수 선택법
- All possible regressions
  - 변수들의 가능한 모든 조합으로부터 최적의 모형을 찾아냄
  - 유의한 변수가 누락되지 않는 안전한 방법
  - 변수가 많을수록 탐색 시간이 급증함
- Forward selection
  - 기여도가 높은 유의한 변수부터 하나씩 추가하는 방법
  - 빠른 계산
  - 이미 선택된 변수는 다시 제거되지 않음
- Backward selection
  - 모든 변수를 포함한 상태에서 불필요한 변수를 제거하는 방법
  - 중요한 변수가 제외될 확률이 작음
  - 이미 제외된 변수는 다시 선택되지 않음

### 문제 풀이

![image](https://github.com/eileenjang/statistics/assets/82510378/76a87757-414b-4053-b0b9-b11aa48d0bd9)

5개의 독립변수와 1개의 종속변수가 있으며, 지역과 집 스타일은 범주형 데이터이고, 크기, 침실 개수, 화장실 개수는 양적 데이터이다.
첫 행의 회귀식은 634 = b1*A + b2*1600 + b3*4 + b4*2 + b5*ranch이다. 이 회귀식에서는 독립변수에 숫자가 아닌 값이 들어있기 때문에 범주형 데이터를 숫자로 표현하는 방법에 대해서도 이후 알아보아야 한다.

- 양적 데이터만을 사용해 선형회귀를 해보면 아래와 같다.
```
import numpy as np
import pandas as pd
import statsmodels.api as sm;

df = pd.read_csv('house_prices.csv')
df.head()

df['intercept'] = 1
lm_bed = sms.OLS(df['price'], df[['intercept', 'bedrooms']])
results_bed = lm_bed.fit()
results_bed.summary()
```

![image](https://github.com/eileenjang/statistics/assets/82510378/c6631914-55ad-4459-9582-8602d129fbe6)

bedroom 변수의 p-value는 0이기 때문에 통계적으로 유의미한 결과이고, 계수가 양수이기 때문에 bedrooms와 price는 양의 상관관계를 가진다.

```
mlr = sms.OLS(df['price'], df[['intercept', 'area', 'bedrooms', 'bathrooms']])
results_mlr = mlr.fit()
results_mlr.summary()
```

![image](https://github.com/eileenjang/statistics/assets/82510378/84e43d6d-b20f-4111-a536-ee755e121ea1)

area 독립변수만 p-value가 0으로 유의하고 이때의 R-squared 값은 1보다 작다. 또한 bedrooms의 계수가 음수로 바뀌었다.
각각 모델링했을 때와 달리 한번에 모델링을 했을 때 결과가 다른 이유는 다중 공선성 때문이다.

### 다중 선형 회귀 계수

![image](https://github.com/eileenjang/statistics/assets/82510378/62b17970-8e0f-420e-9451-c64052357689)

X'는 X의 전치행렬이고 X-1는 X의 역행렬이다.

```
X = df[['intercept', 'bathrooms', 'bedrooms', 'area']]
y = df['price']
np.dot(np.dot(np.linalg.inv(np.dot(X.transpose(), X)), X.transpose()), y)

>> array([10072.10704671,  7345.3917137 , -2925.80632467,   345.91101884])
```
선형대수로 도출한 계수와 OLS로 도출한 계수가 같음을 확인할 수 있다.
