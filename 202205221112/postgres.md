# Relational Database (PostgreSQL)

Login to PostgreSQL:
```sql
psql --username=<user-name> dbname=<db-name>
```
See list of database:
`
\l
`
Create database:
```sql
CREATE DATABASE database_name;
```
Connect to database:
```
\c database_name
```
Display tables:
`
\d
`
Create a table in the database:
```sql
CREATE TABLE table_name();
CREATE TABLE table_name(column_name DATATYPE CONSTRAINTS);

```
View more details of a table:
`
\d table_name
`
Add a column to table:
```sql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE;
```
Delete a column from the table:
```sql
ALTER TABLE table_name DROP COLUMN column_name;
```
Data type:
```sql
NUMERIC(4,1) // four digits before the decimal and one digit after the decimal
DATE
SERIAL
INT
VARCHAR(30)
```
> ***Serial*** type will make the column datatype an `INT` with a `NOT NULL` constraint and automatically increment the integer when a new row is added.
Constraints:
```sql
NOT NULL
```
Rename column:
```sql
ALTER TABLE table_name RENAME COLUMN column_name TO new_name;
```
Add data to table:
```sql
INSERT INTO table_name(column_1, column_2) VALUES(value1, value2);
```
View table:
```sql
SELECT * FROM table_name;
```
Delete a row:
```sql
DELETE FROM table_name WHERE condition;
```
Delete table:
```sql
DROP TABLE table_name;
```
Rename a database:
```sql
ALTER DATABASE database_name RENAME TO new_database_name;
```
Update a row:
```sql
UPDATE table_name SET column_name=new_value WHERE condition;
```
View table in order (row):
```sql
SELECT columns FROM table_name ORDER BY column_name;
SELECT * FROM table_name ORDER BY column_name;
```
Set primary key:
```sql
ALTER TABLE table_name ADD PRIMARY KEY(column_name);
ALTER TABLE table_name ADD PRIMARY KEY(column1, column2);

```
Drop constraint:
You can find `constraint_name` with `\d table_name`.
```sql
ALTER TABLE table_name DROP CONSTRAINT constraint_name;
```
Set foreign key:
```sql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE REFERENCES referenced_table_name(referenced_column_name);
ALTER TABLE table_name ADD COLUMN column_name DATATYPE CONSTRAINT REFERENCES referenced_table_name(referenced_column_name);
ALTER TABLE table_name ADD FOREIGN KEY(column_name) REFERENCES referenced_table(referenced_column);
```
Enforce constraint:
```sql
ALTER TABLE table_name ADD UNIQUE(column_name);
ALTER TABLE table_name ALTER COLUMN column_name SET NOT NULL;
```
Join tables:
```sql
SELECT columns FROM table_1 FULL JOIN table_2 ON table_1.primary_key_column = table_2.foreign_key_column;

SELECT columns FROM junction_table
FULL JOIN table_1 ON junction_table.foreign_key_column = table_1.primary_key_column
FULL JOIN table_2 ON junction_table.foreign_key_column = table_2.primary_key_column;
```









