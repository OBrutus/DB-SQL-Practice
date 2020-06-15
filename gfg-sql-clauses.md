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


# ARITHMETIC EXPRESSION
	If we perform any arithmetic operation on **NULL**, then answer is always **NULL**

# WHERE 
