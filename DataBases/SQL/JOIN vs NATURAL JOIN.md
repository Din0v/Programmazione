# JOIN vs NATURAL JOIN

```SQL
`SELECT * FROM Orders NATURAL JOIN Customers;`

`SELECT Orders.OrderID, Customers.FirstName, Customers.LastName, ProductName, Quantity  FROM Orders  JOIN Customers  ON Orders.CustomerID = Customers.CustomerID;`
```

la differenza sta nel datatype, natural join connette le colonne dello stesso data type 


### Tags 
#Databases 
#SQL
