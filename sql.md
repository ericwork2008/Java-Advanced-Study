# SQL

## Basic

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
//function
SELECT COUNT(*), `id` FROM `table` GROUP BY xxx;
```

