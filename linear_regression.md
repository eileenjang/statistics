## 회귀 분석

어떤 변수들(X1, X2, X3...) 이 한 변수(Y)의 원인이 되는지 분석하는 방법

### 회귀 분석의 종류

- 독립변수의 수에 따라 "단순회귀분석" vs "다중회귀분석"
- 독립변수의 척도에 따라 "일반회귀분석" vs "더미변수를 이용한 회귀분석"
- 독립변수와 종속변수의 관계에 따라 "선형회귀분석" vs "비선형회귀분석"

#### 단순선형회귀분석의 예

독립변수가 1개이고, 두 변수의 관계를 직선으로 파악한다.
![image](https://github.com/eileenjang/statistics/assets/82510378/26f0db8c-9ac4-4dfc-8c2d-0be2a0504916)

X, Y 관계를 가장 합리적으로 나타내기 위해서는 진차 (y좌표와 같은 x좌표를 갖는 직선 위의 y좌표)의 제곱의 합이 가장 작은 직선을 구해야 한다.

#### 최소 제곱법

진차의 제곱의 합을 구하면 이 식은 다변수 함수이며, 이의 최솟값을 구하기 위해 편미분 또는 행렬을 사용할 수 있다.

## 회귀식
<img width="113" alt="image" src="https://github.com/eileenjang/statistics/assets/82510378/f2a91c47-73dc-4696-813a-f94a3b8ca62c">

- 회귀 분석은 두 변수가 만들어내는 일정 패턴으로 무엇인가를 예측하는 것이기 때문에, y에는 ^ (예측값) 이 들어간다.
- 위 회귀식은 y절편인 b0과 기울기인 b1이 있고, b1을 구하기 위해 최소제곱법을 사용한다.
<img width="350" alt="image" src="https://github.com/eileenjang/statistics/assets/82510378/64b8cfcd-8677-4527-a1e9-fa6803dde637">

- y절편을 구할 때에는 각 변수의 평균을 사용한다.
<img width="144" alt="image" src="https://github.com/eileenjang/statistics/assets/82510378/edaf1270-4d4b-47e8-8b3d-36eb5033d369">

## 회귀 분석 문제 풀이

Q. 소득에 따른 신용카드 사용량을 알아보기 위해 무작위로 몇 명을 뽑아 월 소득 대비 신용카드 사용량을 조사하였더니 아래와 같이 나왔다. 그럼 해당 자료를 바탕으로 회귀식을 구하고, 월 소득이 250만원일 때 신용카드 사용량이 얼마인지 예측하시오.

<img width="352" alt="image" src="https://github.com/eileenjang/statistics/assets/82510378/4ab3db59-e132-43fc-83d6-2c168f72d61e">

- x 평균: 300, y 평균: 100
<img width="494" alt="image" src="https://github.com/eileenjang/statistics/assets/82510378/634620f1-2d9b-4715-89a8-09b57db508a1">

- 기울기 b1 = 0.417, y 절편 b0 = 100 = 0.417 * 300 = - 25.1
- 회귀식: y^ = -25.1 + 0.417x
- y^ = 79.15

## 회귀 분석 예측 구간

회귀식으로 구한 예측값은 점 추정치이기 때문에 예측값을 신뢰하기에 한계가 있어 신뢰구간이라는 개념이 등장한다.

<img width="391" alt="image" src="https://github.com/eileenjang/statistics/assets/82510378/7e4b53fb-4a87-4f44-b5d6-31d9f28019ec">

예측구간을 구할 때는 t분포를 사용하고 자유도는 n-2이다. 이는 변수가 x, y 두개이기 때문에 각 변수 -1을 하면 최종적으로 -2이며 이는 오차제곱합이라 불린다.

<img width="534" alt="image" src="https://github.com/eileenjang/statistics/assets/82510378/dc073c3d-2408-4bf5-b379-df81b74c410c">

## 회귀 분석 예측 구간 문제 풀이

Q. 소득에 따른 신용카드 사용량을 알아보기 위하여 무작위로 몇 명을 뽑아, 월 소득 대비 신용카드 사용량을 조사하였더니 아래와 같이 나왔다. 그리고 해당 자료를 바탕으로 회귀식을 구하였더니 y^=-25.1+0.417x가 나왔고, 이 회귀식을 활용해서 월 소득이 250만원일 때, 카드 사용량은 79.15 만원이 될 것으로 예측하였다.
이때 카드 사용량에 대해서 95%의 예측구간을 설정하시오.

<img width="371" alt="image" src="https://github.com/eileenjang/statistics/assets/82510378/af6f1200-cc8c-4f85-8b4e-38d0cc198b5b">

<img width="548" alt="image" src="https://github.com/eileenjang/statistics/assets/82510378/11a52e7a-6b67-4811-a7d0-340b90f01865">

- y^ = 79.15이고 x0 = 250
- 95% 신뢰구간이므로 a/2 = 0.025이고 자유도는 5-2=3이다.

<img width="382" alt="image" src="https://github.com/eileenjang/statistics/assets/82510378/3473e8fa-fef4-4141-95d7-5fd953277343">
