# HAVING vs WHERE

1. $HAVING$: filters entire group and is similar to $WHERE$

2. $WHERE$: is used to set a condition and filters individual rows 
```sql 
SELECT region, SUM(revenue) AS total_revenue  
FROM sales 
GROUP BY region 
HAVING total_revenue > 100;
```

[[AS in sql]]: is like assigning a variable after an operation be it a "sum" or anything else, variables are called "aliases"


### Tags 
#Databases 
#MySQL 

