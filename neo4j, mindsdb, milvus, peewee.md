---
title: 'neo4j, mindsdb, milvus, peewee'
created: '2022-11-09T16:43:16.660Z'
modified: '2022-11-11T10:01:50.099Z'
---

# neo4j, mindsdb, milvus, peewee

## peewee

### docs

[official doc](http://docs.peewee-orm.com/)

## milvus

### docs

[official doc](https://milvus.io/docs)

## neo4j

### OGM, object-graph mapping

[activegraph](https://github.com/neo4jrb/activegraph)

[cypher](https://github.com/bratushka/cypher)

[neomodel](https://github.com/neo4j-contrib/neomodel)

[neode](https://github.com/adam-cowley/neode)

### docs

[graph data science](https://neo4j.com/docs/graph-data-science/current/operations-reference/algorithm-references/)

[python driver doc](https://neo4j.com/docs/python-manual/current/get-started/)

### drivers

[neo4j python driver](https://github.com/neo4j/neo4j-python-driver)

[neo4j python graph data science driver](https://github.com/neo4j/graph-data-science-client)

### wrappers

[pypher](https://github.com/emehrkay/Pypher) cypher builder in python [intro](https://neo4j.com/blog/express-cypher-queries-pure-python-pypher/)

[neopy](https://github.com/pawamoy/neopy)

[pygds](https://github.com/stellasia/pygds) a python wrapper to call Neo4j Graph Data Science procedures from python using the Neo4j python driver

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

[sqlalchemy 2.0 doc](https://docs.sqlalchemy.org/en/20/tutorial/engine.html)

[pypika](https://pypika.readthedocs.io/en/latest/) sql query builder

[mindsdb native](https://github.com/mindsdb/mindsdb_native)

[mindsdb python sdk](https://github.com/mindsdb/mindsdb_python_sdk)
