# Export CSV from PostgreSQL Table

*Source: [Export a PostgreSQL Table to a CSV File](https://www.postgresqltutorial.com/export-postgresql-table-to-csv-file/)*

## Contents

* [Walkthrough](Export%20CSV%20from%20PostgreSQL%20Table.md#walkthrough)
* \[\[\#Export Data from a Table to CSV using `\COPY` Command|Export Data from a Table to CSV using `\COPY` Command\]\]
* [Appendix: Links](Export%20CSV%20from%20PostgreSQL%20Table.md#appendix-links)

## Walkthrough

The easiest way to export data of a table to a CSV file is to use `COPY` statement. For example, if you want to export the data of the `persons` table to a CSV file named `persons_db.csv` in the `C:\tmp` folder, you can use the following statement:

````SQL
COPY persons TO 'C:\tmp\persons_db.csv' DELIMITER ',' CSV HEADER;
````

PostgreSQL exports all data from all columns of the `persons` table to the `persons_db.csv` file.

![postgresql export csv](https://www.postgresqltutorial.com/wp-content/uploads/2015/05/postgresql-export-csv.jpg)

In some cases, you want to export data from just some columns of a table to a CSV file. To do this, you specify the column names together with table name after `COPY` keyword. For example, the following statement exports data from the `first_name`, `last_name`, and `email`  columns of the `persons` table to `person_partial_db.csv`

````SQL
COPY persons(first_name,last_name,email) 
TO 'C:\tmp\persons_partial_db.csv' DELIMITER ',' CSV HEADER;
````

![postgresql export csv partially](https://www.postgresqltutorial.com/wp-content/uploads/2015/05/postgresql-export-csv-partially.jpg)

If you don’t want to export the header, which contains the column names of the table, just remove the `HEADER` flag in the `COPY` statement. The following statement exports only data from the `email` column of the `persons` table to a CSV file.

````SQL
COPY persons(email) 
TO 'C:\tmp\persons_email_db.csv' DELIMITER ',' CSV;
````

![postgresql export csv partially without header](https://www.postgresqltutorial.com/wp-content/uploads/2015/05/postgresql-export-csv-partially-without-header.jpg)

Notice that the CSV file name that you specify in the `COPY` command must be written directly by the server. It means that the CSV file must reside on the database server machine, not your local machine. The CSV file also needs to be writable by the user that PostgreSQL server runs as.

## Export Data from a Table to CSV using `\COPY` Command

In case you have the access to a remote PostgreSQL database server, but you don’t have sufficient privileges to write to a file on it, you can use the PostgreSQL built-in command `\copy`.

The `\copy` command basically runs the `COPY` statement above. However, instead of server writing the CSV file, psql writes the CSV file, transfers data from the server to your local file system. To use `\copy` command, you just need to have sufficient privileges to your local machine. It does not require PostgreSQL superuser privileges.

For example, if you want to export all data of the `persons` table into `persons_client.csv` file, you can execute the `\copy` command from the psql client as follows:

````shell
\copy (SELECT * FROM persons) to 'C:\tmp\persons_client.csv' with csv
````

---

## Appendix: Links

* [PostgreSQL](../3-Resources/Tools/Developer%20Tools/Data%20Stack/Databases/PostgreSQL.md)
* [Data Engineering](../2-Areas/MOCs/Data%20Engineering.md)
* [Databases](../2-Areas/MOCs/Databases.md)
* [SQL](../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/SQL.md)
* [ETL](ETL.md)
* [ELT](ELT.md)
* [SQL](../3-Resources/Tools/Developer%20Tools/Data%20Stack/Procedural%20Languages/SQL.md)
* [Data Science](../2-Areas/MOCs/Data%20Science.md)

*Backlinks:*

````dataview
list from [[Export CSV from PostgreSQL Table]] AND -"Changelog"
````
