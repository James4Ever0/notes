---
tags: [graph database, pyjom, self-learning, syntax]
title: Neo4j learning notes
created: '2022-06-03T02:05:00.000Z'
modified: '2022-08-18T08:03:43.211Z'
---

# Neo4j learning notes

[neo4j desktop](https://neo4j.com/download) provide free multi graph databases support, enable you to create and use multiple graph datases at once

to query undirected relationships:
match () -- (p) return p

create fulltext index
create fulltext index lucene for (n:Person) on each [n.title, n.description]
call db.index.fulltext.queryNodes("titlesAndDescriptions", "Full Metal Jacket") yield node, score return node, score

calculate customer rating cosine similarity for recommendation:
https://neo4j.com/graphgists/northwind-recommendation-engine
match (c1:customer)-[r1:rated]-(:product)-[r2:rated]-(c2:customer)
with sum(r1.score*r2.score) as dot_product,
sqrt(reduce(x=0, a in r1.score | x+a^2)) as r1_length,
sqrt(reduce(y=0, b in r2.score | y+b^2)) as r2_length
merge (c1)-[s:similarity}]-(c2)
set s +=  {score:dot_product/(r1_length*r2_length)

use collect to turn maps into lists:
match (p) return collect(p.names)

exist subquery:
match (n:Person) where exists {
match (n) --(t:Tech)
where size((t)-[:likes]-(:Person)) >2
}
return n.name

list comprehension:
return [x in range(0,10) where x%3 = 0| x/2] as list
return [x in range(0,10) where not x in range(4,10) |x ] as list

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

plus can concatenate strings

tenporal dataformat can be used as numbers to compute.

Map operators
. for static value access by key, [] for dynamic value access by key

List operators
+ for concatenation, IN to check existence of an element in a list, [] for accessing element(s) dynamically

recommendation steps:
first find targets by meta relatonships
next sort recommendation by frequency, ratings or occurance
third filter items by topics or properties
