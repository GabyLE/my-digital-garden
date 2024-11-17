---
{"dg-publish":true,"permalink":"/data-scientist/categorical-data-type-in-pandas/","created":"2023-11-06T00:44:33.496+01:00","updated":"2024-03-02T14:56:10.000+01:00"}
---


- `Categoricals` are a pandas type corresponding to categorical variables in statistics.
- All values of categorical data are either in `categories` or `np.nan` 
- Order is defined by the order of `categories`, not lexical order of the values.
- The data structure consists of a `categories` array and an integer array of `codes` which point to the real values in the `categories` array.
## Useful when:
- A string variable consist of only a few different values. Converted will save memory.
- The lexical order of a variable is not the same as the logical order ("one", "two", "three").
- Telling oder Python libraries that the column should be treated as a categorical variable.