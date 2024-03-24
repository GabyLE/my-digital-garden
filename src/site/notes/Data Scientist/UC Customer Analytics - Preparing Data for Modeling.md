---
{"dg-publish":true,"permalink":"/data-scientist/uc-customer-analytics-preparing-data-for-modeling/","created":"2023-11-05T16:11:47.159-05:00","updated":"2024-03-02T08:54:58.948-05:00"}
---


#datacamp-project #datascience 
## Concepts
- **Proof-of-concept:** (POC) is a demonstration of a product in which work is focused on determining whether an idea can be turned into a reality. Rather than focusing on building or developing the idea, it tests whether the idea is feasible and viable. [source](https://www.techtarget.com/searchcio/definition/proof-of-concept-POC)
- Nominal Data: is a type of [[Data Scientist/categorical data\|categorical data]] that consists of categories that can't be ordered or ranked. It has an specific [[Data Scientist/categorical data type in pandas\|categorical data type in pandas]].
## Queries
### Checking column if data type int 64
```python
dtype == np.int64
```
[source](https://pandas.pydata.org/docs/reference/api/pandas.api.types.is_int64_dtype.html)
## Changing column to nominal categorical data type
```python
# changing nominal categories
nominal_columns = ['gender', 'relevant_experience', 'enrolled_university', 'major_discipline', 'company_type']

for col in nominal_columns:
    ds_jobs[col] = ds_jobs[col].astype("category")
    
ds_jobs[nominal_columns].dtypes
```

## Converting column to ordered categorical data type
```python
# converting ordered categories
education_level = ['Primary School', 'High School', 'Graduate', 'Masters', 'Phd']

ds_jobs['education_level'] = pd.Categorical(ds_jobs['education_level'], categories=education_level, ordered=True)

ds_jobs['education_level'].dtype
```

## Filtering DataFrames on ordered categorical columns
Ordered categorical columns can be filtered in the same way as numerical columns, using comparison operators such as `>`.
```python
mask = (ds_jobs_clean['experience'] >= '10') & (ds_jobs_clean['company_size'] >= '1000-4999')

ds_jobs_clean = ds_jobs_clean[mask]

ds_jobs_clean.shape
```

## Subject
[[Data Scientist/Machine Learning\|Machine Learning]]
[[°Pandas\|°Pandas]]
[[Data Scientist/Numpy\|Numpy]]


