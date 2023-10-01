# SQL

## REFERENCE

{% embed url="https://www.w3schools.com/sql/" %}

## Basic

{% embed url="https://www.nupanch.com/blog/the-easy-way-to-read-sql" %}

From above blog, it explain the easyway to read the SQL

```
the database management system follows a specific order of execution -
FROM (including any joins)
WHERE
GROUP BY
HAVING
SELECT
ORDER BY
```

Basic query syntax

```
SELECT 'col' FROM 'table';
INSERT INTO `table` (`id`, `name`, `age`) VALUES (x, 'x', x), (x, 'x', x);
SELECT `col1`, `col2` FROM `table`;
UPDATE `table` SET `col1` = 'x' WHERE `col2` = 2;
DELETE FROM `table` WHERE `id` = 1;
```

## Misc

1.  enum value&#x20;

    ```sql
    col = 'Y'
    ```
2. MySQL uses three-valued logic -- TRUE, FALSE and UNKNOWN. Anything compared to NULL evaluates to the third value: UNKNOWN. That “anything” includes NULL itself!
3. IF

```
IF(condition, value_if_true, value_if_false) AS xxx
```

4. Regular Expression

```
NOT REGEXP '^S'
or 
NOT LIKE 'S%'
```

5. SELECT extra

```

SELECT DISTINCT * FROM `table` LIMIT 3 OFFSET 1;
SELECT * FROM `table` ORDER BY id;
SELECT * FROM `table` ORDER BY id1 ASC, id2 DESC;
SELECT * FROM `table` ORDER BY id DESC;
//function COUNT, SUM, AVG, MIN, MAX, 
SELECT COUNT(*), `id` FROM `table` GROUP BY xxx;
```

6. `WHERE` & HAVING

[https://www.geeksforgeeks.org/difference-between-where-and-having-clause-in-sql/](https://www.geeksforgeeks.org/difference-between-where-and-having-clause-in-sql/)

```
only supports columns that already exist in this table.
Don't support columns in AS 

But HAVING can use the columns in AS, but HAVING have performance issue
```
