# SQL - PostgreSQL - Get the Last Element of an Array

*Source: [sql-snippets/get-last-array-element.md at main · count/sql-snippets (github.com)](https://github.com/count/sql-snippets/blob/main/postgres/get-last-array-element.md)*

Explore this snippet [here](https://count.co/n/0loHJW60YO8?vm=e).

## Description

Use the `array_length` function to access the final element of an array. This function takes two arguments, an array and a dimension index. For common one-dimensional arrays, the dimension index is always `1`.

````sql
with data as (select array[1,2,3,4] as nums)

select nums[array_length(nums, 1)] from data
````

---

## Appendix: Links

* *Code*
* [SQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/SQL.md)
* [Databases](../../../MOCs/Databases.md)
* [PostgreSQL](../../../../3-Resources/Tools/Developer%20Tools/Data%20Stack/Databases/PostgreSQL.md)
* [Development](../../../MOCs/Development.md)

*Backlinks:*

````dataview
list from [[SQL - PostgreSQL - Get the Last Element of an Array]] AND -"Changelog"
````
