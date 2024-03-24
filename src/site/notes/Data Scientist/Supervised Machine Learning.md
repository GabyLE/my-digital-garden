---
{"dg-publish":true,"permalink":"/data-scientist/supervised-machine-learning/","created":"2023-11-09T14:57:12.884-05:00","updated":"2024-03-02T08:39:30.854-05:00"}
---


>[!info] what?
>Supervised machine learning learns patterns and relationships between input and output data. It is defined by its use of labeled data. A labeled data is a dataset that contains a lot of examples of Features and Target. Supervised learning uses algorithms that learn the relationship of Features and Target from the dataset. This process is referred to as Training or Fitting.^[https://www.datacamp.com/blog/supervised-machine-learning]
## What is it?
*Para realizar la predicción, en aprendizaje automático supervisado, el modelo encuentra relaciones entre los datos de entrada (features) y los de salida (variable objetivo o a predecir). A diferencia del no supervisado ([[Unsupervised Machine Learning\|Unsupervised Machine Learning]]), que solo toma los datos de entrada y realizar una predicción/clasificación propia.*

There are two types of supervised learning algorithms:
1. Classification
2. Regression
![Classification-Regression](https://i.imgur.com/6NI8DKD.png)
## Classification
- The algorithm learn to predict an outcome or event in the future.
- Predicts discrete outcomes.
- 2 outcomes (0/1, true/false, yes/no) -> Binary Classification
- 2+ outcomes -> Multiclass Classification
- Algorithms for classification tasks:
	- [[Data Scientist/Logistic Regression\|Logistic Regression]]
	- [[°Decision Tree Classifier\|°Decision Tree Classifier]]
	- [[K Nearest Neighbor Classifier\|K Nearest Neighbor Classifier]]
	- [[Random Forest Classifier\|Random Forest Classifier]]
	- [[°Neural Networks\|°Neural Networks]]

## Regression
- Learn from the data to predict continuous values.
- Some algorithms:
	- [[Data Scientist/Linear Regression\|Linear Regression]]
	- [[Data Scientist/Decision Tree\|Decision Tree]]
	- [[°K Nearest Neighbor Regressor\|°K Nearest Neighbor Regressor]]
	- [[°Random Forest Regressor\|°Random Forest Regressor]]
	- [[°Neural Networks\|°Neural Networks]]
## Characteristics
- Unlike [[Unsupervised Machine Learning\|Unsupervised Machine Learning]], it uses labeled data. Meaning, the data contains both the Features (X variables) and the Target (y variable).
- SLM typically produce more accurate results than unsupervised learning.
- Require more human involment at the outset in order to correctly identify the data.
- Goal: forecast results for new data based on a model that has learned from labeled training dataset.
- Compare to unsupervised, it is straightforward.
## Subjects
[[Data Scientist/Machine Learning\|Machine Learning]]




