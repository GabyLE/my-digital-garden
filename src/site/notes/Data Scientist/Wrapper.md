---
{"dg-publish":true,"permalink":"/data-scientist/wrapper/","created":"2023-11-14T22:10:10.862+01:00","updated":"2024-03-02T14:58:59.132+01:00"}
---


## Case
**Instantiate a linear kernel SVR estimator**
```python
# Import modules
from sklearn.svm import SVR
from sklearn.feature_selection import RFECV

# Instantiate estimator and feature selector
svr_mod = SVR(kernel="linear")
feat_selector = RFECV(svr_mod, cv=5)

# Fit
feat_selector = feat_selector.fit(X, y)

# Print support and ranking
print(feat_selector.support_)
print(feat_selector.ranking_)
print(X.columns)
```
- `SVR`
	- `kernel = 'linear'`
- `RFECV`
	- `cv`: cross validations
**Drop unimportant column found in step 2 from `X` and instantiate a `larsCV` object**
```python
# Import modules
from sklearn.linear_model import LarsCV

# Drop feature suggested not important in step 2
X = X.drop('sex', axis=1)

# Instantiate
lars_mod = LarsCV(cv=5, normalize=False)

# Fit
feat_selector = lars_mod.fit(X, y)

# Print r-squared score and estimated alpha
print(lars_mod.score(X, y))
print(lars_mod.alpha_)
```
- `LarsCV`


## Related
[[Data Scientist/Feature Selection (Regression Models)\|Feature Selection (Regression Models)]]
[[Data Scientist/Regression Models\|Regression Models]]
[[Data Scientist/Machine Learning\|Machine Learning]]
[[Data Scientist/Data Scientist\|Data Scientist]]