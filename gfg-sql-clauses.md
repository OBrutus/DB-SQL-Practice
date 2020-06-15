# WITH
	Ex 1.
	```
	WITH temporaryTable(averageValue) as
		(SELECT avg(Salary)
		from Employee), 
		    SELECT EmployeeID,Name, Salary 
		    FROM Employee, temporaryTable 
		    WHERE Employee.Salary > temporaryTable.averageValue
	```
	Ex 2.
	```	    
	WITH TTT(AAA) AS  
		( SELECT AVG(Population) FROM City ) 
	SELECT Name, Population 
	FROM City, TTT 
	WHERE City.Population > TTT.AAA;
	```
	
    The SQL WITH clause is good when used with complex SQL statements rather than simple ones
    It also allows you to break down complex SQL queries into smaller ones which make it easy for debugging and processing the complex queries.
    The SQL WITH clause is basically a drop-in replacement to the normal sub-query.

----------

# ARITHMETIC EXPRESSION
	If we perform any arithmetic operation on **NULL**, then answer is always **NULL**

----------

# WHERE 
	```
		SELECT * FROM [table_name] **WHERE** [condition]
	```
	condition can include operators as follow
	operators 
		```
			>	>=
			<	<=
			=	<>
			BETWEEN
			LIKE
			IN
		```
----------

# WHERE v/s HAVING
	The where clause works on row’s data, not on aggregated data.

	Ex:
		table marks: 
			Student       Course      Score

		```SELECT Student, Score FROM Marks WHERE Score >=40 ```

		```SELECT Student, SUM(score) AS total FROM Marks GROUP BY Student HAVING total > 70```

----------

# INTERSECT 
	This implies the result contains all the rows which are common to both the SELECT statements

	Syntax :
	```
		SELECT column-1, column-2 …… 
		FROM table 1
		WHERE…..

		INTERSECT

		SELECT column-1, column-2 …… 
		FROM table 2
		WHERE…..
	```
----------

# EXCEPT
	contains all the rows except the common rows of the two SELECT statements
	Ex.
	```
	SELECT ID, Name, Bonus 
	FROM
	table1 
	LEFT JOIN
	table2
	ON table1.ID = table2.Employee_ID

	EXCEPT

	SELECT ID, Name, Bonus 
	FROM
	table1 
	RIGHT JOIN
	table2
	ON table1.ID = table2.Employee_ID;
	```
----------

# JOINS
## INNER JOINS
	The INNER JOIN keyword selects all rows from both the tables as long as the condition satisfies. This keyword will create the result-set by combining all rows from both the tables where the condition satisfies i.e value of the common field will be same.

	```
		USE classicmodels;

		select customers.customerName, customers.city, payments.paymentDate 
		from customers INNER join payments 
		on customers.customerNumber = payments.customerNumber
	```


## LEFT JOIN 
	This join returns all the rows of the table on the left side of the join and matching rows for the table on the right side of join. The rows for which there is no matching row on right side, the result-set will contain null. LEFT JOIN is also known as LEFT OUTER JOIN

	```
		USE classicmodels;
		select customers.customerName, customers.city, payments.paymentDate 
		from customers LEFT join payments 
		on customers.customerNumber = payments.customerNumber
	```

## RIGHT JOIN
	This join returns all the rows of the table on the right side of the join and matching rows for the table on the left side of join. The rows for which there is no matching row on left side, the result-set will contain null. RIGHT JOIN is also known as RIGHT OUTER JOIN.

	```
		USE classicmodels;
		select customers.customerName, customers.city, payments.paymentDate 
		from customers RIGHT join payments 
		on customers.customerNumber = payments.customerNumber
	```

## FULL JOIN 
	FULL JOIN creates the result-set by combining result of both LEFT JOIN and RIGHT JOIN. The result-set will contain all the rows from both the tables. The rows for which there is no matching, the result-set will contain NULL values.

	```
		USE classicmodels;
		select customers.customerName, customers.city, payments.paymentDate 
		from customers FULL join payments 
		on customers.customerNumber = payments.customerNumber
	```