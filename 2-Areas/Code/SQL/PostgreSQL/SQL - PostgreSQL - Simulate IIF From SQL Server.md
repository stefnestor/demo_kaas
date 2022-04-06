# SQL - PostgreSQL - Simulate IIF From SQL Server

*Source: https://wiki.postgresql.org/wiki/Simulating_iif_function*

Some developers are accustomed to some 'Access' (and others db's) functions. One of them is the `iif` function that works very simple and sometimes add to the query more intelligence.

Well, you will surprising to know that in [PostgreSQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Databases/PostgreSQL.md) is possible and is quite simple to add this function.

In plain [SQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/SQL.md): 

````SQL
CREATE OR REPLACE FUNCTION iif_sql(boolean, anyelement, anyelement) returns anyelement as
$body$ select case $1 when true then $2 else $3 end $body$
LANGUAGE sql IMMUTABLE;
````

while you can cover all data types at once with this *polymorphic function*, the type needs to be defined or specified using casts. 

A simple `iif_sql(8<9,'yes','no')` will fail.

To solve this, you could add an overloaded method to cover this specific case: 

````SQL
CREATE OR REPLACE FUNCTION iif_sql(boolean, unknown, unknown) returns text as
$body$ select case $1 when true then textin(unknownout($2)) else ﻿﻿textin(unknownout($3)) end $body$
LANGUAGE sql IMMUTABLE;
````

In [PL/Pgsql](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/PLPGSQL.md):

````SQL
CREATE OR REPLACE FUNCTION iif_(boolean, double precision, double precision) RETURNS double precision AS
$body$
DECLARE
	rtVal double precision;
BEGIN
	rtVal := (select case $1 when true then $2 else $3 end);
	return rtVal;
END;
$body$
LANGUAGE 'plpgsql' IMMUTABLE CALLED ON NULL INPUT SECURITY INVOKER;
````

---

## Appendix: Links

* *Code*
* [SQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/SQL.md)
* [Databases](../../../MOCs/Databases.md)
* [PostgreSQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Databases/PostgreSQL.md)
* [PLPGSQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/PLPGSQL.md)
* [Development](../../../MOCs/Development.md)

*Backlinks:*

````dataview
list from [[SQL - Simulate `IIF` in PostgreSQL]] AND -"Changelog"
````
