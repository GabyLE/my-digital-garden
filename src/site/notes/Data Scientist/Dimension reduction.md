---
{"dg-publish":true,"permalink":"/data-scientist/dimension-reduction/","created":"2023-11-11T18:10:13.836+01:00","updated":"2024-03-02T15:11:20.000+01:00"}
---


- A way to reduce dimensionality of a dataset is by only selecting relevant features in the dataset.
	- [[Data Scientist/Feature Selection (Regression Models)\|Feature Selection (Regression Models)]]
## Sklearn
**Case:** You are supplied with a dataset assigned to the variable `scaled_data`. This dataset exhibits high dimensionality, you need to reduce it to 3 features.
```python
from sklearn.decomposition import PCA

reducing_fn = PCA(n_components=3)

reducing_fn.fit(scaled_data)

reduced_ft = reducing_fn.transform(scaled_data)

print(reduced_ft.shape)
```