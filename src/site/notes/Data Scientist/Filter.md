---
{"dg-publish":true,"permalink":"/data-scientist/filter/","created":"2023-11-14T15:41:43.383-05:00","updated":"2024-03-02T08:58:39.219-05:00"}
---


## Case # 1
Here you'll practice a filter method on the `diabetes` DataFrame followed by 2 different styles of wrapper methods that include cross-validation. You will be using `pandas`, `matplotlib.pyplot` and `seaborn` to visualize correlations, process your data and apply feature selection techniques to your dataset.
The feature matrix with the dropped target variable column (`progression`) is loaded as `X`, while the target variable is loaded as `y`.
![](https://i.imgur.com/OmrsvjM.png)

**Correlation Matrix**
```python
# Create correlation matrix and print it
cor = diabetes.corr()
print(cor)

# Correlation matrix heatmap
plt.figure()
sns.heatmap(cor, annot=True, cmap=plt.cm.Reds)
plt.show()

# Correlation with output variable
cor_target = abs(cor["progression"])

# Selecting highly correlated features
best_features = cor_target[ cor_target > 0.5]
print(best_features)
```
## Related
[[Data Scientist/Feature Selection (Regression Models)\|Feature Selection (Regression Models)]]
[[Data Scientist/Regression Models\|Regression Models]]
[[Data Scientist/Machine Learning\|Machine Learning]]
[[Data Scientist/Data Scientist\|Data Scientist]]