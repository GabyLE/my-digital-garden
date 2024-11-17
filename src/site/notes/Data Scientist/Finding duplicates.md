---
{"dg-publish":true,"permalink":"/data-scientist/finding-duplicates/","created":"2023-11-07T20:36:44.244+01:00","updated":"2024-03-02T15:12:44.351+01:00"}
---


## From different sources using threshold
- For comparing pair records, the class `recordlinkage.Compare` is used, from the `recordlinkage` library. 
>[!info] [[Data Scientist/Record Linkage\|Record Linkage]]
> Procedure of bring information of two or more sources from entities that one believes are the same.
### Generate pairs
```python
indexer = recordlinkage.Index()
indexer.block('initials') # 'initials' are the rule used to block
candidate_links = indexer.index(dfA, dfB)
```
### Compare
Finding the duplicates.
```python
import recordlinkage

comp_cl = recordlinkage.Compare()
comp_cl.string('listed_in', 'listed_in', label='listed_in', threshold=0.3)

potential_matches = comp_cl.compute(pairs, productions_old, productions_new)

print(potential_matches)
```
## Rewriting data
```python
tv.loc[tv['seasons'] > 2, 'seasons'] = 2
print(tv.head())
```

[[Data Scientist/Data Scientist\|Data Scientist]]