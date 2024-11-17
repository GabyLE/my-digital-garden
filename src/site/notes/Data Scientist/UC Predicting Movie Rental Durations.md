---
{"dg-publish":true,"permalink":"/data-scientist/uc-predicting-movie-rental-durations/","created":"2023-11-07T22:23:35.056+01:00","updated":"2024-03-02T14:54:21.952+01:00"}
---


>Recommend a model yielding a [[Data Scientist/mean squared error\|mean squared error]] _(MSE) less than 3_ on the _test set_
## Imports
```python
import pandas as pd
import numpy as np

from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error

import matplotlib.pyplot as plt
import seaborn as sns
```
- Data management: [[°Pandas\|°Pandas]] , [[Data Scientist/Numpy\|Numpy]]
- Machine learning: [[°Sklearn\|°Sklearn]]
- Data visualization: [[°Matplotlib\|°Matplotlib]], [[Data Scientist/Seaborn\|Seaborn]]
## Convert column to date format
```python
import pandas as pd

# Load the dataset
df = pd.read_csv("dataset.csv")

# Convert the date column to date format
df["date"] = pd.to_datetime(df["date"])
```
In the above code snippet, we first load the dataset using the `read_csv()` function provided by [[°Pandas\|°Pandas]]. Next, we use the `to_datetime()` function to convert the “date” column to date format. The `to_datetime()` function returns a [[°Pandas datetime object\|°Pandas datetime object]], which we assign back to the “date” column of the dataframe.

## Dummy variables
```python
# dummy variables from 'special_features'
# data format: {Trailers,"Deleted Scenes","Behind the Scenes"}

rental_info['deleted_scenes'] = np.where(rental_info['special_features'].str.contains('Deleted Scenes'), 1, 0)

rental_info[['deleted_scenes', 'special_features']].sample(5)
```
Using the numpy function `where` and the String object function `contains` to look for the string "Deleted Scenes" in the column. Then set to `1` when is found and `0` when not.
## Performing feature selection
For this task, the [[Data Scientist/LASSO regression\|LASSO regression]] technique is used.
```python
# import lasso reg
from sklearn.linear_model import Lasso
# lasso instance
lasso = Lasso(alpha=1, random_state=9)

# train the model
lasso.fit(X_train, y_train)
lasso_coef = lasso.coef_

# Perform feature selectino by choosing columns with positive coefficients
X_lasso_train, X_lasso_test = X_train.iloc[:, lasso_coef > 0], X_test.iloc[:, lasso_coef > 0]
```
## Choosing models
Since the objective is to predict the number of days the customer will take to return the movie, this target value requires for a regression model. Some algorithms for regression are:
- [[Data Scientist/Linear Regression\|Linear Regression]]
- [[Data Scientist/Decision Tree\|Decision Tree]] Regressor
- [[Data Scientist/Random Forest\|Random Forest]] Regressor
### Linear Regression
```python
# linear regression
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

lin_reg = LinearRegression()
lin_reg.fit(X_lasso_train, y_train)
y_test_pred = lin_reg.predict(X_lasso_test)
mse_lin_reg_lasso = mean_squared_error(y_test, y_test_pred)
mse_lin_reg_lasso
```
### Decision Tree Regressor
```python
# Decision Tree Regressor
from sklearn.tree import DecisionTreeRegressor
from sklearn.model_selection import RandomizedSearchCV

# Decision Tree hyperparameter space
param_dist_dt = {'max_depth': [2,3,4], 
                'min_samples_leaf': [0.12,0.14,0.16,0.18]}

# intance decision tree regressor
dt = DecisionTreeRegressor()

# find the best hyperparameters
rand_search_dt = RandomizedSearchCV(dt,
                                   param_distributions=param_dist_dt,
                                   cv=5,
                                   random_state=9)

# fit the random search
rand_search_dt.fit(X_train, y_train)

# variable for the best hyperparameters
hyper_params_dt = rand_search_dt.best_params_

# run on chosen paramsn
dt = DecisionTreeRegressor(max_depth=hyper_params_dt['max_depth'],
                          min_samples_leaf=hyper_params_dt['min_samples_leaf'],
                          random_state=9)

# fit
dt.fit(X_train, y_train)
y_dt_pred = dt.predict(X_test)
mse_decision_tree = mean_squared_error(y_test, y_dt_pred)
mse_decision_tree
```
- `RandomizedSearchCV`: Finding the best hyperparameters
- Hyperparameters
	- `max_depth`:
	- `min_samples_leaf`:
### Random Forest Regressor
```python
# Random forest regressor
from sklearn.ensemble import RandomForestRegressor

# Random forest hyperparameter space
param_dist_rf = {'n_estimators': np.arange(1,101,1),
          'max_depth':np.arange(1,11,1)}

# Create a random forest regressor
rf = RandomForestRegressor()

# Use random search to find the best hyperparameters
rand_search_rf = RandomizedSearchCV(rf, 
                                 param_distributions=param_dist_rf, 
                                 cv=5, 
                                 random_state=9)

# Fit the random search object to the data
rand_search_rf.fit(X_train, y_train)

# Create a variable for the best hyper param
hyper_params_rf = rand_search_rf.best_params_

# Run the random forest on the chosen hyper parameters
rf = RandomForestRegressor(n_estimators=hyper_params_rf["n_estimators"], 
                           max_depth=hyper_params_rf["max_depth"], 
                           random_state=9)
rf.fit(X_train,y_train)
y_rf_pred = rf.predict(X_test)
mse_random_forest= mean_squared_error(y_test, y_rf_pred)
mse_random_forest
```
- `RandomizedSearchCV`: Finding the best hyperparameters
- Hyperparameters
	- `n_estimators`:
	- `max_depth`:

## Subjects
[[Data Scientist/Machine Learning\|Machine Learning]]
[[Data Scientist/Data Scientist\|Data Scientist]]
