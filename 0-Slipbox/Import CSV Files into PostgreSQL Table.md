# Import CSV Files into PostgreSQL Table

*Source: [Import CSV File Into PosgreSQL Table](https://www.postgresqltutorial.com/import-csv-file-into-posgresql-table/)*

See Also:

* [Export CSV from PostgreSQL Table](Export%20CSV%20from%20PostgreSQL%20Table.md)

## Contents

* [Introduction](Import%20CSV%20Files%20into%20PostgreSQL%20Table.md#introduction)
* \[\[\#Import a CSV file into a table using `COPY` statement|Import a CSV file into a table using `COPY` statement\]\]
* [Details](Import%20CSV%20Files%20into%20PostgreSQL%20Table.md#details)
* [Import CSV file into a table using pgAdmin](Import%20CSV%20Files%20into%20PostgreSQL%20Table.md#import-csv-file-into-a-table-using-pgadmin)
* [Appendix: Links](Import%20CSV%20Files%20into%20PostgreSQL%20Table.md#appendix-links)

## Introduction

First, [create a new table](https://www.postgresqltutorial.com/postgresql-create-table/) named `persons` with the following columns:

* `id`: the person id
* `first_name`: first name
* `last_name:` last name
* `dob` date of birth
* `email`: the email address

````SQL
CREATE TABLE persons (
  id SERIAL,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  dob DATE,
  email VARCHAR(255),
  PRIMARY KEY (id)
)
````

![posgresql import csv](https://www.postgresqltutorial.com/wp-content/uploads/2015/05/posgresql-import-csv.jpg)

Second, prepare a CSV data file with the following format:

![csv data](https://www.postgresqltutorial.com/wp-content/uploads/2015/05/csv-data.jpg)

![csv file](https://www.postgresqltutorial.com/wp-content/uploads/2015/05/csv-file.jpg)

The path of the CSV file is as follows: `C:\sampledb\persons.csv`

## Import a CSV file into a table using `COPY` statement

To import this CSV file into the `persons` table, you use `COPY` statement as follows:

````SQL
COPY persons(first_name, last_name, dob, email)
FROM 'C:\sampledb\persons.csv'
DELIMITER ','
CSV HEADER;`
````

PostgreSQL gives back the following message:

````shell
COPY 2
````

It means that two rows have been copied. Let’s check the `persons` table.

````SQL
SELECT * FROM persons;
````

![](https://www.postgresqltutorial.com/wp-content/uploads/2020/07/PostgreSQL-Import-CSV.png)

It works as expected.

## Details

Let’s dive into the `COPY` statement in more detail.

First, you specify the table with column names after the `COPY` keyword. The order of the columns must be the same as the ones in the CSV file. In case the CSV file contains all columns of the table, you don’t need to specify them explicitly, for example:

````SQL
COPY sample_table_name
FROM 'C:\sampledb\sample_data.csv' 
DELIMITER ',' 
CSV HEADER;`
````

Second, you put the CSV file path after the `FROM` keyword. Because CSV file format is used, you need to specify `DELIMITER` as well as `CSV` clauses.

Third, specify the `HEADER` keyword to indicate that the CSV file contains a header. When the `COPY` command imports data, it ignores the header of the file.

Notice that the file must be read directly by the PostgreSQL server, not by the client application. Therefore, it must be accessible by the PostgreSQL server machine. Also, you need to have superuser access in order to execute the `COPY` statement successfully.

## Import CSV file into a table using pgAdmin

See Also: [PgAdmin](../3-Resources/Tools/Developer%20Tools/Data%20Stack/Database%20GUI/PgAdmin.md)

In case you need to import a CSV file from your computer into a table on the PostgreSQL database server, you can use the pgAdmin.

The following statement [truncates](https://www.postgresqltutorial.com/postgresql-truncate-table/) the `persons` table so that you can re-import the data.

````SQL
TRUNCATE TABLE persons 
RESTART IDENTITY;
````

First, right-click the `persons` table and select the **Import/Export…** menu item:

![](https://www.postgresqltutorial.com/wp-content/uploads/2020/07/PostgreSQL-Import-CSV-pgAdmin-Step-1.png)

Second, (1) switch to import, (2) browse to the import file, (3) select the format as CSV, (4) select the delimiter as comma (`,`):

![](https://www.postgresqltutorial.com/wp-content/uploads/2020/07/PostgreSQL-Import-CSV-pgAdmin-Step-2.png)

Third, click the columns tab, uncheck the id column, and click the OK button:

![](https://www.postgresqltutorial.com/wp-content/uploads/2020/07/PostgreSQL-Import-CSV-pgAdmin-Step-3.png)

Finally, wait for the import process to complete. The following shows the dialog that inform you the progress of the import:

![](https://www.postgresqltutorial.com/wp-content/uploads/2020/07/PostgreSQL-Import-CSV-pgAdmin-Step-4.png)

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
list from [[Import CSV Files into PostgreSQL Table]] AND -"Changelog"
````
