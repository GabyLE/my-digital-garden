---
{"dg-publish":true,"permalink":"/regular-expressions/","created":"2024-02-04T11:06:56.442-05:00","updated":"2024-03-02T09:11:39.587-05:00"}
---


- String with special syntax
- Allow to match patterns
- Uses:
	- Find 
	- Parse
	- Remove/replace
- Python library: `re` 
## Regex patterns
![](https://i.imgur.com/cCaaX0f.png)

## Python's re module
- `re` module
- `split`: split a string on regex
- `findall`: find all patterns in a string
- `search`: search for a pattern
- `match`: match an entire string or substring based on a pattern
- Pattern first, and the string second.
- May return a iterator, string or match object.
``` python
re.split('\s+', 'Split on spaces')
>>> ['Split', 'on', 'spaces']
```

