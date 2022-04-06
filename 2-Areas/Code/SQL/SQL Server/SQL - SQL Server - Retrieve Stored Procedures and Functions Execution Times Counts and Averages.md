# SQL - Retrieve Stored Procedures and Functions Execution Times Counts and Averages

*Source: [Retrieve Stored Procedures and Functions Execution Time, Count, and Average | thiscodeWorks](https://www.thiscodeworks.com/61faf1cfb783be0015bbaf78)*

*Note: time is in Micro-Seconds*

````SQL
/* STORED PROCEDURES AND FUNCTIONS EXECUTION TIME, COUNT AND AVERAGE */
 
SELECT DB_NAME(st.dbid) DBName
      ,OBJECT_SCHEMA_NAME(st.objectid,dbid) SchemaName
      ,OBJECT_NAME(st.objectid,dbid) StoredProcedure
      ,max(cp.usecounts) Execution_count
      ,sum(qs.total_worker_time) total_cpu_time
      ,sum(qs.total_worker_time) / (max(cp.usecounts) * 1.0)  avg_cpu_time
 
FROM sys.dm_exec_cached_plans cp join sys.dm_exec_query_stats qs on cp.plan_handle = qs.plan_handle
     CROSS APPLY sys.dm_exec_sql_text(cp.plan_handle) st
where DB_NAME(st.dbid) is not null and cp.objtype = 'proc'
group by DB_NAME(st.dbid),OBJECT_SCHEMA_NAME(objectid,st.dbid), OBJECT_NAME(objectid,st.dbid) 
order by sum(qs.total_worker_time) desc;
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
list from [[SQL - Retrieve Stored Procedures and Functions Execution Times Counts and Averages]] AND -"Changelog"
````
