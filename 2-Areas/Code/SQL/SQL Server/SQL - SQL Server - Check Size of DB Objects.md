# SQL - Check Size of DB Objects

*Source: [Check Size of DB Objects | thiscodeWorks](https://www.thiscodeworks.com/61faf29db783be0015bbaf7f)*

````SQL
/* CHECK SIZE OF DB OBJECTS */
SELECT TOP(10)
      o.[object_id]
    , obj = SCHEMA_NAME(o.[schema_id]) + '.' + o.name
    , o.[type]
    , i.total_rows
    , i.total_size
FROM sys.objects o
JOIN (
    SELECT
          i.[object_id]
        , total_size = CAST(SUM(a.total_pages) * 8. / 1024 AS DECIMAL(18,2))
        , total_rows = SUM(CASE WHEN i.index_id IN (0, 1) AND a.[type] = 1 THEN p.[rows] END)
    FROM sys.indexes i
    JOIN sys.partitions p ON i.[object_id] = p.[object_id] AND i.index_id = p.index_id
    JOIN sys.allocation_units a ON p.[partition_id] = a.container_id
    WHERE i.is_disabled = 0
        AND i.is_hypothetical = 0
    GROUP BY i.[object_id]
) i ON o.[object_id] = i.[object_id]
WHERE o.[type] IN ('V', 'U', 'S')
ORDER BY i.total_size DESC;
````

---

## Appendix: Links

* *Code*
* [SQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/SQL.md)
* [Databases](../../../MOCs/Databases.md)
* [SQL Server](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Databases/SQL%20Server.md)
* [Development](../../../MOCs/Development.md)

*Backlinks:*

````dataview
list from [[SQL - Check Size of DB Objects]] AND -"Changelog"
````
