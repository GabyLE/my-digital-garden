---
{"dg-publish":true,"permalink":"/data-scientist/polynomial-features/","created":"2023-11-11T18:33:23.674+01:00","updated":"2024-03-02T15:13:31.000+01:00"}
---


## Single Cases
- An array `X` with tow features has been loaded for you along with the target variable array `y`. Fit a multiple linear regression model with **interaction terms** on the target variable `y` as a function of the feature variables contained in `X`.
  ```python
import pandas as pd
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures

interacction_term = PolynomialFeatures(degree=2, interaction_only=True, include_bias=False)
X_inter = interaction_term.fit_transfom(X)

model = LinearRegression()
model.fit(X_inter,y)

print('Regression coefficients: {}'.format(model.coef_))
```

## Subjects
[[Data Scientist/Machine Learning\|Machine Learning]]