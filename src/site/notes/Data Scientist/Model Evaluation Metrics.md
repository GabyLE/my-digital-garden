---
{"dg-publish":true,"permalink":"/data-scientist/model-evaluation-metrics/","created":"2023-11-14T16:25:48.887-05:00","updated":"2024-03-02T09:13:47.259-05:00"}
---


- Asses the performance and effectiveness of a statistical or machine learning model.
	- How well is performing
	- Comparing different models or algorithms.
- What to asses:
	- Predictive ability
	- Generalization capability
	- Overall quality
- Choosing an evaluation metric depends on:
	- Problem domain
	- Type of data
	- Desired outcome
- Objective of the model: **Give a high accuracy_score on out-of-sample data**

## For Classification
Depending on the output, two algorithms can be used:
1. **Class output:** When is a binary classification problem, the output is either 0 or 1. Algorithms: SVM and [[K Nearest Neighbor Classifier\|K Nearest Neighbor Classifier]]
2. **Probability output:** It gives probability outputs. Algorithms: [[Data Scientist/Logistic Regression\|Logistic Regression]], [[Random Forest Classifier\|Random Forest Classifier]], Gradient Boosting, Adaboost, etc. Converting probability outputs to class outputs can be done with a probability threshold.

## For Regression
Doesn´t depend on the output. The output is always continuous and requires no further treatment. 
## More ...
https://www.analyticsvidhya.com/blog/2019/08/11-important-model-evaluation-error-metrics/
https://neptune.ai/blog/ml-model-evaluation-and-selection

## Related
[[Data Scientist/Machine Learning\|Machine Learning]]
[[Data Scientist/Data Scientist\|Data Scientist]]