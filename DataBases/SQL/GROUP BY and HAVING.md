# the relation between Group By and Having

> [!warning]
> they usually follow each other :) 

```SQL 
SELECT region, SUM(revenue) total_revenue 
FROM sales 
GROUP BY region 
HAVING total_revenue > 100;
```

### Tags 
#Databases 
#SQL 
