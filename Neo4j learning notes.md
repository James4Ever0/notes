---
created: 2022-06-03T10:05:00+08:00
modified: 2022-06-03T11:26:15+08:00
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

simple case expression:
match(n)
return
case n.eyes
when "blue" then 1
when "brown" then 2
else 3
end as result

generic case expression
match (n)
return 
case
when n.eyes = "blue" then 1
when n.age > 40 then 2
else 3 // if without else then return null
end as result

inequality symbol: <>

mutating updating node properties:
match(n)
set n+={name:"helen"} // if using = the properties will be totally replaced instead of update.
return n.name

merge can only ensure the existance of one node or pattern at a time, no comma

Map operators
. for static value access by key, [] for dynamic value access by key

List operators
+ for concatenation, IN to check existence of an element in a list, [] for accessing element(s) dynamically
