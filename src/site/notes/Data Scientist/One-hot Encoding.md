---
{"dg-publish":true,"permalink":"/data-scientist/one-hot-encoding/","created":"2023-11-12T21:56:50.766+01:00","updated":"2024-09-14T18:17:10.999+02:00"}
---


- What to use `sklearn` or `pandas`: https://towardsdatascience.com/one-hot-encoding-scikit-vs-pandas-2133775567b8
- Example: https://www.geeksforgeeks.org/ml-one-hot-encoding/

## Use Case
```python
from sklearn.preprocessing import OneHotEncoder

ohe_columnas = ['StateHoliday', 'StoreType']

ohe_categorias = [['none', 'a', 'b', 'c'], ['a', 'b', 'c', 'd']]

  

# todos los datos tipo str

X[ohe_columnas] = X[ohe_columnas].astype(str)

X_input[ohe_columnas] = X_input[ohe_columnas].astype(str)

enc = OneHotEncoder(sparse_output=False)

one_hot_encoded = enc.fit_transform(X[ohe_columnas])

one_hot_encoded_input = enc.transform(X_input[ohe_columnas])


#Create a DataFrame with the one-hot encoded columns

#We use get_feature_names_out() to get the column names for the encoded data

one_hot_df = pd.DataFrame(one_hot_encoded, columns=enc.get_feature_names_out(ohe_columnas))

one_hot_df_input = pd.DataFrame(one_hot_encoded_input, columns=enc.get_feature_names_out(ohe_columnas))

# Concatenate the one-hot encoded dataframe with the original dataframe

df_encoded = pd.concat([X, one_hot_df], axis=1)

df_encoded_input = pd.concat([X_input, one_hot_df_input], axis=1)

# Drop the original categorical columns

df_encoded = df_encoded.drop(ohe_columnas, axis=1)

df_encoded_input = df_encoded_input.drop(ohe_columnas, axis=1)

# Display the resulting dataframe

print('Columnas test: ', df_encoded_input.columns)

print('Columnas train: ', df_encoded.columns)
```



## Subject
[[Data Scientist/Machine Learning\|Machine Learning]]
[[Data Scientist/Data Scientist\|Data Scientist]]

