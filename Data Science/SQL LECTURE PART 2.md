# SQL LECTURE PART 2
### 2/22

* the relations (Tables) are what we say 
* database management system is a layer of abstraction -- optimizing the data structures and implementation

Thought process for running:
from --> where (apply selection) --> group by (form groups and aggregate) --> having (eliminate **groups**) --> select (project away columns, just keeping thosed used in select, group by, and having) --> \[distinct\] (applied to select statement, eliminate duplicates)

Database
* server
* software
* library 

Multidimension Data Model
* Fact Table
  * minimizes redundant info
  * reduces data errors 
* Dimensions (more data based on Fact Table)
  * easy to manage and summarize
  * easy to rename
* connect the above tables with **join**

How to bring tables together with **join**
* without specification, just bringing together tables results in cartesian product of their rows
* use `where` to filter
```SQL
SELECT S.sname, R.day
FROM Reserves AS r, Sailors AS s
WHERE S.sid = R.sid
```
*the above matches and selects rows only where the `sid` match*

* `WHERE` can take booleans like `s1.age > s2.age`
* can even self-join if using same table multiple times. In which the range boolean above would be useful 

### types of joins
* `INNER` (aka Natural) is default
  * matches where values intersect
  * possible ways to write:
```SQL
FROM Sailors s INNER JOIN Reserves r
ON s.sid = r.sid
WHERE s.age > 20;

#or
FROM Sailors s NATURAL JOIN Reserves r
WHERE s.age > 20;

#or
FROM Sailors s, Reserves r
WHERE s.sid = r.sid
AND s.age > 20;
```

* `OUTER` is optional for Left, Right, and Full joins. 
  * example: LEFT OUTER = LEFT 
* `LEFT` returns the matched rows, **and** preserves all unmatches rows from the table on the left of the join clause (uses nulls in field of non-matching tuples). 
  * matches on intersection of values, with additional unmatched rows on left table
* `RIGHT` is similar to the above but returns the unmatches rows from the table on the right of the clause. Filling in null for missing values from the left table.
* `FULL JOIN` returns all matched or unmatches rows from the tables on both sides of the join clause
  * fills in null values for missing values on both sides
  
**every datatype in sql can be null**
*as comparator*
If using `NULL` as comparator, the query will return `null`. In a `where` statement, it evaluates to false. Must use `IS NULL` and `IS NOT NULL`. Null values are not actual values and are not used in aggregation an such. Use `IS NULL` for refined selection in `JOIN` when you don't want the intersections.
```SQL
SELECT *
FROM TableA A
LEFT JOIN TableB B
ON A.Key = B.Key
WHERE B.Key IS NULL 
```
Will select all the A.Key that does not intersect with B.Key

SQL aggregations functions: `min`, `max`, `count`, `sum`, `avg`, `stddev`, and `variance`.

### using `limit`
* relations have no intrinsic order -- using `limit` will result in arbitrary choice. 
* therefore, data input order may be biased and not representative of other rows 
* it can return any rows, and then any different rows as output for a query 

### case 
To transform data. Like an `if` statement in pythong
```SQL
CASE WHEN transaction > 0 THEN log(transaction)
  WHEN transaction = - THEN 0
  ELSE -1*transaction
END AS log_amt
```
Transforms data and puts in new column 

### WITH
Use `WITH` to create new table that can be chained together with existing table. Helpful for querying 
```SQL
WITH new_table_name AS
(
  normal SQL selections and queries 
)
SELECT *
FROM table, new_table_name 
... 
...
```
Selects data from the exisiting and new table



























  
  
  
  


 
  