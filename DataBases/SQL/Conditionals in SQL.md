# Conditionals in SQL 

```SQL 
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ...
    ELSE default_result
END
```

example 

```SQL 
SELECT name, salary,
   CASE
      WHEN salary > 50000 THEN 1 /*Cosa deve confrontare*/
      ELSE 0
   END AS high_earner /*Salva nuova VAR*/
FROM employees;
```

### Tags 
#Databases 
#MySQL 