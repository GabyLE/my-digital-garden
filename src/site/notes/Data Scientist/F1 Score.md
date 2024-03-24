---
{"dg-publish":true,"permalink":"/data-scientist/f1-score/","created":"2023-11-17T04:51:30.391-05:00","updated":"2024-03-02T09:32:43.630-05:00"}
---


- When for a use case, we are trying to get the best precision and recall at the same time.
- Harmonic mean of precision and recall values for a **classification problem**
$$
F_{1}= \left( \frac{recall^{-1} + precision^{-1}}{2} \right)^{-1} = 2 \cdot \frac{precision \cdot recall}{precision + recall}
$$
- Harmonic mean punishes extreme values more.
- To give a percentage to add more importance/weight to either precision or recall, an adjustable parameter beta can be include:
$$
F_{\beta} = (1 + \beta^{2}) \cdot \frac{precision \cdot recall}{(\beta^2 \cdot precesion) + recall}
$$
*$F_{\beta}$ measures the effectiveness of a model with respect to a user who attaches $\beta$ times as much importance to recall as precision*

## Sklearn
### Classification report
```python
from sklearn.metrics import classification_report, confusion_matrix

knn = KNeighborsClassifier(n_neighbors=7)

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.4, random_state=42)

knn.fit(X_train, y_train)y_pred = knn.predict(X_test)

print(classification_report(y_test, y_pred))
```

**Output**
![](https://i.imgur.com/84NYhkQ.png)


## Related
[[Data Scientist/Model Evaluation Metrics\|Model Evaluation Metrics]]
[[Data Scientist/Data Scientist\|Data Scientist]]