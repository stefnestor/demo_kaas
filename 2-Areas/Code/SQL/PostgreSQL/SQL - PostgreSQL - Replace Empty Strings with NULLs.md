# SQL - PostgreSQL - Replace Empty Strings with NULLs

*Source: [sql-snippets/replace-empty-strings-null.md at main · count/sql-snippets (github.com)](https://github.com/count/sql-snippets/blob/main/postgres/replace-empty-strings-null.md)*

Explore this snippet [here](https://count.co/n/Fzyv9i4SP2B?vm=e).

## Description

An essential part of cleaning a new data source is deciding how to treat missing values. The [`CASE`](https://www.postgresql.org/docs/current/functions-conditional.html#FUNCTIONS-CASE) statement can help with replacing empty values with something else:

````sql
WITH data AS (
  SELECT *
  FROM (VALUES ('a'), ('b'), (''), ('d')) AS data (str)
)

SELECT
  CASE WHEN LENGTH(str) != 0 THEN str END AS str
FROM data;
````

Output:

|str|
|---|
|a|
|b|
|NULL|
|d|

---

## Appendix: Links

* *Code*
* [SQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/SQL.md)
* [Databases](../../../MOCs/Databases.md)
* [PostgreSQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Databases/PostgreSQL.md)
* [Development](../../../MOCs/Development.md)

*Backlinks:*

````dataview
list from [[SQL - PostgreSQL - Replace Empty Strings with NULLs]] AND -"Changelog"
````
