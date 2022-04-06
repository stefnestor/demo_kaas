# SQL - SQL Server - Monitor Query Plans

*Source: [Monitor Query Plans | thiscodeWorks](https://www.thiscodeworks.com/61faf27fb783be0015bbaf7e)*

````SQL
/* Monitor query plans */
 
SELECT
    highest_cpu_queries.plan_handle,  
    highest_cpu_queries.total_worker_time, 
    q.dbid, 
    q.objectid, 
    q.number, 
    q.encrypted, 
    q.[text] 
FROM 
    (SELECT TOP 50  
        qs.plan_handle,  
        qs.total_worker_time 
     FROM 
        sys.dm_exec_query_stats qs 
     ORDER BY qs.total_worker_time desc) AS highest_cpu_queries 
     CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS q 
ORDER BY highest_cpu_queries.total_worker_time desc;
````

For [SQL Server](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Databases/SQL%20Server.md).

---

## Appendix: Links

* *Code*
* [SQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/SQL.md)
* [Databases](../../../MOCs/Databases.md)
* [SQL Server](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Databases/SQL%20Server.md)
* [Development](../../../MOCs/Development.md)

*Backlinks:*

````dataview
list from [[SQL - Monitor Query Plans]] AND -"Changelog"
````
