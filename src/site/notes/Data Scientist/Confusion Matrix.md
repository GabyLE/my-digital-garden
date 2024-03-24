---
{"dg-publish":true,"permalink":"/data-scientist/confusion-matrix/","created":"2023-11-15T08:33:23.985-05:00","updated":"2024-03-02T09:32:20.023-05:00"}
---


- N x N Matrix, where N is the number of **predicted classes**
- For classification problems, where the output can be two or more classes.
- Measure: 
	- Precision-recall
	- Specificity
	- Accuracy
	- AUC-ROC curves
## Definitions^[https://www.analyticsvidhya.com/blog/2019/08/11-important-model-evaluation-error-metrics/#Confusion_Matrix]
- **True Positive (TP)**: Predicted positive, and it's true.
- **True Negative (TN):** Predicted negative, and it's true.
- **False Positive (FP): (Type 1 Error):** Predicted positive, and it's false.
- **False Negative (FN): (Type 2 Error):** You predicted negative, and it's false.
- **Accuracy:** proportion of total number of correct predictions.  Accuracy is true positives (predicted 1, actual 1) + true negatives (predicted 0, actual 0) divided by the total.
$$
Accuracy = \frac{(TP + TN)}{(TP+TN+FP+FN)}
$$
- **Positive Predictive Value or Precision:** Proportion of **positive** cases that were **correctly** identified. *Casos que fueron predecidos como positivos y son positivos, con respecto a la suma entre los casos predecidos como positivos correctamente y los casos que fueron predecidos negativos, pero son positivos.* Precision is true positives divided by the total number of predicted positive values.
$$
Precision = \frac{TP}{TP+FP}
$$
- **Negative Predictive Value:** Proportion of **negative** cases that were **correctly** identified.*Casos que son predecidos como negativos correctamente, con respecto a la suman entre los casos predecidos negativos correctamente y los casos que fueron predecidos como positivos, pero son negativos.*
$$
Negative Predictive Value = \frac{TN}{TN+FP}
$$
- **Sensitivity or Recall:** Proportion of actual positive cases which are correctly identified. *Casos positivos correctamente predecidos, con respecto a la suma del total de positivos predecidos, correctos e incorrectos.* Recall is true positives divided by the total number of actual positive values.
$$
Sensitivity = \frac{TP}{(TP+FN)}
$$
- **Specificity:** Proportion of actual negative cases which are correctly identify. *Casos negativos correctamente predecidos, con respecto a la suma de total de los casos negativos predecidos, correctos e incorrectos*
$$
Specificity=\frac{TN}{TN+FN}
$$
- **Rate:** Measuring factor in a confusion matrix.
![](https://i.imgur.com/pTEWpoe.png)


## Interpretation
- Depending on the problem, we are concerned with just one of the defined metrics.
	- Pharmaceutical company: could be more concerned with a minimal wrong positive diagnosis --> Specificity.
	- Attrition model will be more concerned with Sensitivity.
## Sklearn
![](https://i.imgur.com/oaEO5ip.png)
### Confusion matrix using `sklearn`
```python
from sklearn.metrics import confusion_matrix

# Create predictions
test_predictions = rfc.predict(X_test)

# Create and print the confusion matrix
cm = confusion_matrix(y_test, test_predictions)
print(cm) # [[TN FP] [FN TP]]

# Print the true positives (actual 1s that were predicted 1s)
print("The number of true positives is: {}".format(cm[1, 1]))
```
### Precision vs. recall
The accuracy metrics you use to evaluate your model should _always_ be based on the specific application. For this example, let's assume you are a really sore loser when it comes to playing Tic-Tac-Toe, but only when you are certain that you are going to win.

Choose the most appropriate accuracy metric, either precision or recall, to complete this example. But remember, _if you think you are going to win, you better win!_

Use `rfc`, which is a random forest classification model built on the `tic_tac_toe` dataset.

```python
from sklearn.metrics import precision_score

test_predictions = rfc.predict(X_test)

# Create precision or recall score based on the metric you imported
score = precision_score(y_test, test_predictions)

# Print the final result
print("The precision value is {0:.2f}".format(score))
```

[Sklearn documentation](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html)
## Related
[[Data Scientist/Model Evaluation Metrics\|Model Evaluation Metrics]]
[[Data Scientist/Data Scientist\|Data Scientist]]