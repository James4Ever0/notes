---
created: 2022-06-03T10:05:00+08:00
modified: 2022-06-03T10:37:49+08:00
---

# Neo4j learning notes

to query undirected relationships:
match () -- (p) return p

to use conditional matches or regular expressions:
match () -- (p) where p.name in ["helen"] or p.name =~ ".*chinese.*" return p

create index on properties:
create index for (n:Category) on (n.categoryName)

asterisks:

load csv:
load csv with headers from "http://localhost/person.csv" as line
call {with line
merge (n:person {id: toInteger(line.id)})
set n.name = line.name
} in transactions of 2 rows

count nodes:
match (n) return count(n)

match relationship patterns:
match (n) -[:friend|hater*3]->(p) return p limit 20

node can have multiple labels, while relationship can only have one type, both specified after the colon.
