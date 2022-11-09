---
title: 'neo4j, mindsdb, milvus, peewee'
created: '2022-11-09T16:43:16.660Z'
modified: '2022-11-09T17:21:24.584Z'
---

# neo4j, mindsdb, milvus, peewee

## neo4j

### docs

[graph data science](https://neo4j.com/docs/graph-data-science/current/operations-reference/algorithm-references/)

### drivers

[neo4j python driver](https://github.com/neo4j/neo4j-python-driver)

### wrappers

[neopy](https://github.com/pawamoy/neopy)

## mindsdb

since mindsdb is sql-based it is time to create monkey patches for sqlalchemy core?

```python
from sqlalchemy import text
  
# write the SQL query inside the text() block
sql = text('SELECT * from BOOKS WHERE BOOKS.book_price > 50')
results = engine.execute(sql)
```

### tools

[Lightwood](https://github.com/mindsdb/lightwood) is an AutoML framework that enables you to generate and customize machine learning pipelines declarative syntax called JSON-AI [doc](https://lightwood.io/)

### docs

[official doc](https://docs.mindsdb.com/)

### wrappers

[mindsdb native](https://github.com/mindsdb/mindsdb_native)

[mindsdb python sdk](https://github.com/mindsdb/mindsdb_python_sdk)
