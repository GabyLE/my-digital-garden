---
{"dg-publish":true,"permalink":"/data-scientist/lasso-regression/","created":"2023-11-08T08:20:55.183-05:00","updated":"2024-03-02T08:59:27.213-05:00"}
---


>Used to estimate the relationships between variables and make predictions. Finding balance between model simplicity and accuracy. Ir achieves this by adding a penalty term to the traditional [[Data Scientist/Linear Regression\|Linear Regression]] , which encourages sparse solutions where some coefficients are forced to be exactly zero. This feature makes LASSO useful for feature selection, as it can automatically identify and discard irrelevant or redundant variables 


- Also L1 regularization
- Stands for **Least Absolute Shrinkage and Selection Operator**

*Busca entre todas las variables, cómo están relacionadas entre ellas y a partir de allí crea un camino para predecir la variable objetivo. Para crear este camino o modelo, toma el modelo de regresión lineal, y elimina algunos características forzando el coeficiente las acompaña a ser cero, esto no lo hacer arbitrariamente, sino que depende de las relaciones que haya determinado, eliminando aquellas características que son redundantes o no aportan mucho al modelo. Al hacer estas eliminaciones, el modelo se vuelve más sencillo sin tener que perder precisión.*

## Characteristics

- Use shrinkage, where data values are shrunk towards a central point as the mean.
- Models are simple and spares, with fewer parameters.
- Well-suited when:
	- High level of multicollinearity
	- Automate parts of model selection, like variable selection/parameter elimination

## How it works^[https://www.mygreatlearning.com/blog/understanding-of-lasso-regression/]

1. Inicia con un model de regresión lineal asumiendo una relación lineal entre las variables independientes.
2. Añade el parámetro L1, el cual es la suma del valor absoluto de los coeficientes estimados de la regresión lineal, multiplicado por un parámetro lambda que puede ser afinado para un ajuste del model.
3. El objetivo de la regresión LASSO, es encontrar los coeficientes que minimicen  la suma de la diferencia al cuadrado entre los valores predecidos y los verdaderos ([[°residual sum of squares\|°residual sum of squares]] ), midiendo el error entre los valores predecidos y los reales.
4. Coeficientes de reducción, usando la regularización L1, algunos coeficientes de la regresión lineal son reducidos a cero. 
5. Selección del parámetro de ajuste $\lambda$ ,  si  $\lambda+++$ entonces $\beta_{n}\rightarrow0$ ,pero si es muy pequeño, la regulación es mínima.
6. Model fitting: el algoritmo de optimización comúnmente empleado para minimizar la función objetivo es [[°Coordinate Descent\|°Coordinate Descent]], el cual itera sobre cada componente manteniendo los demás fijos.
---
## Subject
[[Data Scientist/Machine Learning\|Machine Learning]]
## Use cases
[[Data Scientist/UC Predicting Movie Rental Durations\|UC Predicting Movie Rental Durations]]
## Python
[Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Lasso.html)
