## 비선형 회귀분석

비선형 회귀분석은 독립변수와 종속변수가 비선형관계일 때 사용하는 분석방법이다. 곡선의 형태를 가질 수도 있기 때문에 `log` 나 `거듭제곱` 을 취해보며 적합한 모델을 찾는다.

```
> df_lm2 <- lm(weight ~ I(day^3) + I(day^2) + day, data=df)
> summary(df_lm2)

Call:
lm(formula = weight ~ I(day^3) + I(day^2) + day, data = df)

Residuals:
    Min      1Q  Median      3Q     Max 
-61.315 -22.821  -1.336  22.511  48.772 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  1.170e+02  1.348e+01   8.683 1.59e-12 ***
I(day^3)    -2.529e-02  4.929e-04 -51.312  < 2e-16 ***
I(day^2)     2.624e+00  5.321e-02  49.314  < 2e-16 ***
day         -1.530e+01  1.632e+00  -9.373 9.51e-14 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 26.69 on 66 degrees of freedom
Multiple R-squared:  0.9995,	Adjusted R-squared:  0.9995 
F-statistic: 4.407e+04 on 3 and 66 DF,  p-value: < 2.2e-16
```

비선형 회귀분석 결과 R-squared가 0.9995로 나타났고 산점도는 아래와 같다.

![image](https://github.com/eileenjang/statistics/assets/82510378/33b60a53-5df6-4d34-bdf4-ece28ec1cbfc)

산점도와 회귀곡선이 거의 일치하며 회귀모델의 수식은 weight = -0.025*day^3 + 2.624*day^2 - 15.298*day + 117.014이다.

## Reference
https://velog.io/@ddoddo/%EB%B9%84%EC%84%A0%ED%98%95-%ED%9A%8C%EA%B7%80%EB%B6%84%EC%84%9D
