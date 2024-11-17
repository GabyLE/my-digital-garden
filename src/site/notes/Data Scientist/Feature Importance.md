---
{"dg-publish":true,"permalink":"/data-scientist/feature-importance/","created":"2023-11-14T22:15:49.016+01:00","updated":"2024-03-02T15:00:27.000+01:00"}
---


## Case # 1
**Random Forest**
```python
# Import
from sklearn.ensemble import RandomForestRegressor

# Instantiate
rf_mod = RandomForestRegressor(max_depth=2, random_state=123, n_estimators=100, oob_score=True)

# Fit
rf_mod.fit(X, y)

# Print
print(diabetes.columns)
print(rf_mod.feature_importances_)
```

**Extra Tree**
```python
# Import
from sklearn.ensemble import ExtraTreesRegressor

# Instantiate
xt_mod = ExtraTreesRegressor()

# Fit
xt_mod.fit(X, y)

# Print
print(diabetes.columns)
print(xt_mod.feature_importances_)
```

