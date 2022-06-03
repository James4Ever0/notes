---
created: 2022-06-03T10:05:00+08:00
modified: 2022-06-03T10:09:41+08:00
---

# Neo4j learning notes

to query undirected relationships:
match () -- (p) return p

to use conditional matches or regular expressions:
match () -- (p) where p.name in ["helen"] or p.name =~ ".*chinese.*" return p

create index on properties:
create index for (n:Category) on (n.categoryName)
