---
{"dg-publish":true,"permalink":"/data-scientist/feature-selection-regression-models/","created":"2023-11-14T21:45:37.707+01:00","updated":"2024-03-02T14:58:24.824+01:00"}
---


- Is considered a pre-processing step.
- Reduces overfitting
- Improves accuracy
- Increases interptretability
- Reduces training time
- Types:
	- Filter: Rank features on statistical performance
	- Wrapper: Use an ML method to evaluate performance
	- Embedded: Iterative model training to extract features
	- Feature importance: for tree-based ML models
- ![](https://i.imgur.com/ZpRvOC0.png)
## [[Data Scientist/Filter\|Filter]]
- The statistical test for the filter method, depend on the type of the feature and response variables.
 
**Feature/Response**  | **Continuous** | **Categorical**
-- | -- | --
Continuous | Pearson's Correlation | LDA
Categorical | ANOVA | Chi-Square

![](https://i.imgur.com/2dMpcws.png)
## [[Data Scientist/Wrapper\|Wrapper]]
1. Forward selection (LARS - least angle regression)
   - Starts with no features, adds one at a time based on their model contribution.
2. Backward elimination
   - Starts with all features, eliminates one at a time, starting with the ones that contributes the least.
3. Bidirectional elimination, combination of forward selection and backward elimination.
4. Recursive feature elimination cross validated
   - RFECV
## Embedded methods
1. [[Data Scientist/LASSO regression\|LASSO regression]]
2. Ridge Regression
3. ElasticNet

- Perform an iterative process, which extracts the features that contribute the most during a given iteration to return the best subset dependent on the penalty  parameter alpha.
![](https://i.imgur.com/rFH64aY.png)

## [[Data Scientist/Feature Importance\|Feature Importance]]
- Are tree-based methods
- [[Data Scientist/Random Forest\|Random Forest]] --> `sklearn.ensemble.RandomForestRegressor`
- Extra Trees --> `sklearn.ensemble.ExtraTreesRegressor`
- After model fit, can be acceses --> `tree_mod.feature_importances_`


![](https://i.imgur.com/gKNF3Ce.png)

## More Resources
[Sklearn Docs](https://scikit-learn.org/stable/modules/feature_selection.html)


## Related
[[Data Scientist/Regression Models\|Regression Models]]
[[Data Scientist/Machine Learning\|Machine Learning]]
[[Data Scientist/Data Scientist\|Data Scientist]]