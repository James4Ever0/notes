---
created: 2022-06-03T10:05:00+08:00
modified: 2022-06-03T14:17:03+08:00
---

# Neo4j learning notes

to query undirected relationships:
match () -- (p) return p

create fulltext index
create fulltext index lucene for (n:Person) on each [n.title, n.description]
call db.index.fulltext.queryNodes("titlesAndDescriptions", "Full Metal Jacket") yield node, score return node, score

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
