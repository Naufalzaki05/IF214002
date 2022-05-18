# Cheat Sheet MySQL
### Users and Privileges Tables
```sql
USER()
CREATE USER 'user'@'localhost';
DROP USER 'user'@'host';
GRANT privileges_names ON object 
TO user;
REVOKE privileges ON object FROM 
user;
ALTER USER user IDENTIFIED BY 
'password';
SET PASSWORD = 'password';
SET PASSWORD FOR 
'user'@'localhost' = 'password';
```

### Databases
```sql
CREATE DATABASE database_name;
USE database_name;
DROP DATABASE database_name;
SHOW DATABASES;
```
### Data Types
```sql
TINYINT
SMALLINT
MEDIUMINT
INT
BIGINT
DECIMAL
FLOAT
DOUBLE
CHAR
VARCHAR
BLOB
DATE
TIME
TIMESTAMP
DATETIME
TINYTEXT
TEXT
LONGTEXT
BIT
BOOL
```
### Tables
```sql
SHOW TABLES;
DESCRIBE table_name
CREATE TABLE table_name ( 
column1 datatype, 
column2 datatype, 
column3 datatype,
);
DROP TABLE table_name;
ALTER TABLE table_name
ADD column_name datatype;
ALTER TABLE table_name
DROP COLUMN column_name;
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
SELECT * FROM table_name;
SELECT column1, column2 ...
FROM table_name;
SELECT DISTINCT column1, column2, ...
FROM table_name;
SELECT column1, column2, ...
FROM table_name
WHERE condition;
SELECT column1, column2, ...
FROM table_name
WHERE condition;
ORDER BY column1 ASC/DESC;
SELECT column1, column2, ...
FROM table_name
WHERE condition;
GROUP BY column1
SELECT column1, column2, ...
FROM table_name
WHERE condition;
LIMIT number_of_results;
SELECT column1, column2, ...
FROM table1
INNER JOIN* table2
ON table1.column_name = table2.column_name;
*LEFT JOIN / RIGHT JOIN / FULL JOIN / SELF JOIN
```
### Indexes
```sql
CREATE INDEX index_name
ON table_name (column1, column2, ...);
CREATE UNIQUE INDEX index_name
ON table_name (column1, column2, ...);
ALTER TABLE table_name
DROP INDEX index_name;
```
### Views
```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
CREATE OR REPLACE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
DROP VIEW view_name;
```
### Date and Time
```sql
DATEDIFF
DAY
DATE_ADD
DATE_SUB
DATE_FORMAT
DAYNAME
DAYWEEK
EXTRACT
LAST_DAY
NOW
MONTH
STR_TO_DATE
SYSDATE
TIMEDIFF
TIMESTAMPDIFF
WEEK
WEEKDAY
YEAR
```
### String
```sql
ASCII
BIN
BIT_LENGHT
CHAR
CHAR_LENGHT
CONCAT
CONCAT_WS
ELT
EXPORT_SET
FIELD
FIND_IN_SET
FORMAT
FROM_BASE64
HEX
INSERT
INSTR
LCASE
LEFT
LENGTH
LIKE
LOAD_FILE
LOCATE
LOWER
LPAD
LTRIM
MAKE_SET
MATCH
MID
NOT_LIKE
NOT_REGEXP
OCT
OCTET_LENGHT
ORD
POSITION
QUOTE
REGEXP
REGEXP_INSTR
REGEXP_LIKE
REGEXP_REPLACE
REGEXP_SUBSTR
REPEAT
REPLACE
REVERSE
RIGHT
RLIKE
RPAD
RTRIM
SOUNDEX
SOUND_LIKE
SPACE
STRCMP
SUBSTR
SUBSTRING_INDEX
TO_BASE64
TRIM
UCASE
UNHEX
UPPER
WEIGHT_STRING
```
### Math
```sql
ABS
ACOS
ASIN
ATAN
CEIL
CONV
COS
COT
CRC32
DEGREES
EXP
FLOOR
LN
LOG
LOG2
LOG10
MOD
PI
POW
POWER
RADIANS
RAND
ROUND
SIGN
SQRT
TAN
TRUNCATE
```
### Aggregate
```sql
AVG
BIT_AND
BIT_OR
BIT_XOR
COUNT
GROUP_CONCAT
JSON_ARRAYAGG
JSON_OBJECTAGG
MAX
MIN
STD
STDDEV
STDDEV_POP
STDDEV_SAMP
SUM
VAR_POP
VAR_SAMP
VARIANCE
```
### Comparison
```sql
>
>=
<
<> (!=)
<=
<=>
=
BETWEEN...AND
COALESCE
GREATEST
IN
INTERVAL
IS
IS_NOT
IS_NOT_NULL
IS_NULL
ISNULL
LIKE
NOT_BETWEEN…AND
NOT_IN
NOT_LIKE
STRCMP
```
### Flow Control
```sql
CASE
IF
IFNULL
NULLIF
```
# Tugas
- Buat infografik / cheatsheet dari perintah-perintah MySQL di atas (boleh yang mau pake PostgreSQL)
- Buat query untuk mencari penduduk berusia diatas 25 tahun yang berada di kabupaten 3204 dari [data ini](https://github.com/insanalamin/IF214002/blob/main/pertemuan10/penduduk.sql)
- Nilai tambah, untuk yang menambahkan perintah-perintah MySQL lainnya
