---
title: numpy and pandas deduplication
created: '2022-09-17T06:49:15.009Z'
modified: '2022-09-17T07:53:42.961Z'
---

# numpy and pandas deduplication

[numpy remove duplicates from array](https://datascienceparichay.com/article/numpy-remove-duplicates-from-array/#:~:text=Use%20the%20np.unique%20%28%29%20function%20to%20remove%20duplicates,remove%20duplicate%20columns%20from%20a%202-D%20Numpy%20array.)

```python
print(np.unique(ar, axis=1))
```

[dupandas](https://pypi.org/project/dupandas/#:~:text=dupandas%20is%20a%20python%20package%20to%20perform%20data,Matchers%20that%20can%20handle%20spelling%20differences%20and%20phonetics.): remove duplicates with custom rules like levenshtein distance, spelling differences and phonetics (fuzzy maching) for english (most likely?)
```bash
pip install dupandas
```

[pandas drop_duplicates](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.drop_duplicates.html)

```python
df.drop_duplicates(subset=['brand', 'style'], keep='last')
```
