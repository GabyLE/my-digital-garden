---
{"dg-publish":true,"permalink":"/data-scientist/handling-outliers/","created":"2023-11-12T05:19:31.802-05:00","updated":"2024-03-02T09:12:17.394-05:00"}
---


- An outlier is an observation far away from other data points.
	- Median house price: $400.000
	- Outlier house price: $5.000.000
- They are extreme values and may not accurately represent the data.
- Can change the mean and standard deviation
- Statistical tests and machine learning models need normally distributed data.
- Should consider why the value is different:
	- There are situations that support them existing -> consider leaving them in the dataset
	- Could there have been an error in data collection -> If so, remove them
- Using descriptive statistics, `df['column'].describe()`, to find if there could be outliers, by comparing the min and max against the mean, and the quartiles.
- Using IQR in box plots:
  ```python
sns.boxplot(data=df, y='column')
plt.show()
```
  ![](https://i.imgur.com/ijWPsFN.png)

## Steps
1. Using the interquartile range:
	- IQR = 75th - 25th percentile
	- Upper Outliers > 75th percentile + (1.5 *  IQR)
	- Lower Outliers < 25th percentile - (1.5 * IQR)
```python
# 75th percentile
seventy_fifth = df['column'].quantile(0.75)

# 25th percentile
twenty_fifth = df['column'].quantile(0.25)

# Interquartile range
df_iqr = seventy_fifth - twenty_fifth
```
2. Identifying outliers
  ```python
# Upperthreshold
upper = seventy_fifth + (1.5 * df_iqr)

# Lower threshold
lower = twenty_fifth - (1.5 * df_iqr)
```
3. Subsetting the data
	```python
df[(df['column'] < lower) | (df['column'] > upper)]
```
4. Dropping outliers
   ```python
no_outliers = salaries[(salaries["Salary_USD"] > lower)  & (salaries["Salary_USD"] < upper)]
```

## Subjects
[[Data Scientist/Data Scientist\|Data Scientist]]
[[Python\|Python]]
