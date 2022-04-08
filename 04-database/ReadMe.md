Avanade Velocity 2022  
# Databases
James.collard@qa.com
---
## General Notes
- T-SQL (Transact SQL) is Microsoft's version of SQL
- Transactional Database is used for everyday data (updating, deleting etc)
- Data Warehouses are a collection of data from databases across the company (used for analysis)


- Before running, write **Use databasename;**
- NB use semicolon at the end of a statement
- Parse means making sure the syntax is correct

- Use -- for a single line comment
Use /* comment here */ for a block comment

- Even though we type Select > From>Where>Order By..., SQL server runs From > Where >select > Orderd by...This means that we cannot use an alias in the WHERE clause (because it is only created in the SELECT clause)

---
## Order of running
1. FROM
2. WHERE
3. GROUP BY (this is where aggregate functions are created)
4. HAVING
5. SELECT
6. ORDER BY

## Concatenate two columns
### e.g. if we wanted to join firstname and lastname together into a fullname column
   
    SELECT firstname + ' ' + lastname as Fullname
    FROM dbo.customers;
 

## Calculations
    SELECT _price * (amountInStock + amountOnOrder) as SalesCalculation
    FROM dbo.products;

## WHERE date='...'
- Best way to enter date is YYYYMMDD regardless of how it is formatted on the table

## NULL
- NULL is an unknown value
- Instead of =NULL, we need to use **is NULL** or **is not NULL** for negatives

## Coalesce function for NULL values
    SELECT address1,address2,county,city + ' ' + coalesce(city,'') as FullAddress
    FROM dbo.Customers;
This is used when we want to replace a NULL value with something else. E.g. above. If we concatenate a few address columns and some city fields are NULL. We can replace this with a blank so the whole address does not show up as NULL

## Between
- BETWEEN value AND value
- This is inclusive of the two values given

## LIKE
- **WHERE city like 'L_'** means any city that starts with L and has one more character
- **WHERE city like 'L__'** means any city that starts with L and has two more characters
- **WHERE city like 'L_%'** means city that has one or more characters
- **WHERE city like 'L[aeiou]'** means city that starts with L and then has a vowel
- **WHERE city like 'L[a-m]** means city that starts with L and has a letter between A and M
- **WHERE city like 'L[a-mo]** means city that starts with L and has a letter between A and M **or** O
- **WHERE city like 'L[^aeiou]'** means city that starts with L and then has anything but a vowel

## SORT
- **Order by** columnname
- **Order by** columnname **DESC** (in descending order)
- **Order by country DESC, city**- this means order by country in descending order. Then order that by city (in normal order)
- NOTE: We can order by up to 16 different columns at a time

## Distinct
    SELECT distinct country FROM dbo.Customers

    SELECT count (distinct country) from dbo.Customers;

This only shows each country once (no duplicates)  
In the 2nd example, the DISTICT goes in the bracket because we are using COUNT

## To get the top 5 or bottom 5 rows
Top 5:
    SELECT top 5 from customers  
Bottom 5: SELECT top 5 from customers **orderby customerID DESC**  
Top 5 based on a particular column: SELECT top 5 FROM customers order by amountPurchased
NOTE: If you want to select the top 5 customers who purchased the most, but two of there are a few who purchased the same amount as the fifth, you can use WITH TIES:
        SELECT top 5 with ties FROM customers

## Creating Tables- some info
- Primary key is unique identifier
- identity (1,1) -> identity is a column we don’t have to populate, the first one means it starts at one and the second one means it increments by 1.
- If using Unicode, do nchar instead of varchar and nvarchar instead of varchar
- Varchar means up to that amount
- Char means it has to be that amount (so Char(4) has to take up 4 characters)
- NOT NULL means the field cannot have a NULL value
- check (workerid<5>) means that it cannot have a value more than 5

## Creating Table- Query
    Create table dbo.workers(
        WorkerID int check (workerid<5>) NOT NULL primary key identity (1,1)
        firstname varchar (30) NOT NULL
        WorkerInfo Varchar (100)
    );

 ## Adding info into a table   
     INSERT into dbo.workers (firstname,workerInfo)
     values ('Niamh', 'Great employee'), ('Doris', 'Poor perfomance'), ('Jane','Good employee');

## Adding info from one table into another
    INSERT into dbo.workers (firstname)
    SELECT firstname from dbo.employees;
This inserts the firstnames in the employee table into the workers table

## Updating Tables/Data
Update dbo.workers, set firstname='Jim', info='Nice person' 
WHERE id=1;

## To Delete
    DELETE dbo.workers
    WHERE id=4;
To delete an entire table, use DROP table

## SUM
    SELECT SUM (freight) as SumOfFreight
    FROM dbo.orders;
This gives the sum of all rows in column freight

## Other Functions- Aggregates
- AVG
- MAX
- MIN
- COUNT
- SUM
- STDEV
- VAR
- VARP
- STDEVP
- There are also more. Just google to find them

e.g. SELECT MIN (freight) as MinFreight from dbo.orders;

## Count
     SELECT count (*) from dbo.employees; (this returns number of rows)

     SELECT count (region) from dbo.employees; (This shows number of employees that have a region that is not NULL)

## Dealing with NULL
    SELECT AVG (coalesce(freight,0)) as AvgF
    FROM dbo.orders;

The AVG function ignores NULLs so it is a good idea to replace NULL with a 0 so it is calculated in the average.

## Dealing with Duplicates
    SELECT count (distinct country) from dbo.customers;

## Using MIN and MAX on words
- Gives the first or last result alphabetically

## Using MIN and MAX on dates
- MIN gives earliest date
- MAX gives latest dates

## GROUPING
    SELECT customerid, sum(freight) as SumF
    FROM dbo.orders
    GROUP BY customerid;

## HAVING
    SELECT customerid, sum(freight) as SumF
    FROM dbo.orders
    GROUP BY customerid
    HAVING sum(freight) >=100;
- HAVING is after GROUP BY (where the aggregates are created) so we can use this to filter, instead of WHERE  
- Only use HAVING when using an aggregate function  
- We can use WHERE as well as HAVING ( e.g. where customerid=1)

## Sometimes 
    SELECT ProductID, sum(quantity * UnitPrice) as 'TotalValue' 
    from dbo.[Order Details]
    GROUP BY ProductID
    HAVING sum(quantity * UnitPrice) <=5000
    ORDER BY TotalValue DESC;
Sometimes we need to use the formula in the WHERE or HAVING clause because the alias is only created in the SELECT clause

## Normalisation
- Getting rid of lots of duplication
- check the course book for info

# JOINS:

- Inner Joins
- Outer Joins (left, right, full, cross)

## Inner Join
    SELECT c.companyname, o.orderdate
    FROM dbo.Customers c INNER JOIN dbo.Orders o
    ON c.Customerid = o.Customerid;
- would be the overlapping bit in a Venn diagram i.e. all customers who have orders and all orders who have customers
- JOIN and INNER JOIN are the same thing

## LEFT OUTER JOIN
    SELECT c.CompanyName, O.OrderDate
    FROM dbo.Customers as c left outer join dbo.orders as o
    ON c.customerid = o.customerid;

- This would give all customers, regardless of whether they have orders or not
- Could also say Left Join instead of Left outer Join
- Right or Left depends on the way you write the tables. in this case, customers is on the left so we get all customers

## Right Outer Join
    SELECT c.CompanyName, O.OrderDate
    FROM dbo.Customers as c right outer join dbo.orders as o
    ON c.customerid = o.customerid;  
- This will give all orders

## Full Outer Join
     SELECT c.CompanyName, O.OrderDate
    FROM dbo.Customers as c Full outer join dbo.orders as o
    ON c.customerid = o.customerid; 
- This shows everything- customers who had/ dont have orders and orders who have/dont have customers

## Cross Join
    SELECT c.CompanyName, O.OrderDate
    FROM dbo.Customers as c cross join dbo.orders as o
- Don't need a ON section
- This would get all the combinations of customers and orders
- Also called a Cartesian product


## Joining more than 2 tables
    SELECT c.CompanyName, O.OrderDate, od.quantity, od.unitprice
    FROM dbo.Customers as c 
        left outer join dbo.orders as o
    ON c.customerid = o.customerid
        Left outer Join dbo.[Order Details] as od
    ON o.OrderID= od.Orderid;
- Just add the next join the same way as the first

## Joining a table to itself (SELF JOIN)
    SELECT E.firstname as Employee
    FROM Employees as e
    INNER JOIN Employees as m
    on E.reportsto=m.employeeID;
- For example, if there is an Employee table with employee ID and reportTo column which shows the employee ID of who they report to. We want to get the name of the employee and the name of the person they report to.

## UNION
    SELECT companyName, city from dbo.Customers
    union
    SELECT companyName,city from dbo.suppliers
    union
    SELECT lastname,city from dbo.Employees;
- This would give a list of all company names and cities from customers,suppliers and employees. It shows them all in one companyName column and one city column
- UNION appends rows, wheras JOINS append columns
- Union sorts the data
- Union hides duplicates

## UNION ALL
- Does not sort the data
- Does not hide duplicate rows
- If you know there are no duplicates, use UNION ALL because it is quicker than UNION

## INTERSECT
    SELECT city from dbo.Customers
    INTERSECT
    SELECT city from dbo.Suppliers;
- This would show all cities that are common to Customers and Suppliers tables
- Removes duplicates and sorts the data

## EXCEPT
     SELECT city from dbo.Customers
    INTERSECT
    SELECT city from dbo.Suppliers;
- This would give a list of cities in the customers table that are not in the suppliers table

# SUB QUERIES

## SELF-CONTAINED
- run another query in a query. You could run them both seperately but this would not be efficient.
- e.g. letterdetails
- Sub query runs first

## Correlated
    SELECT c.CategoryID, c.CategoryName
            (
                SELECT count(p.productID) from dbo.Products as p
                WHERE c.CategoryID=p.CategoryID
            )
    FROM dbo.Categories as c

- Here, the outer query runs first then the sub query because the inner query is dependent on something from the outer query

## Transactions
- Transaction= a unit of work (i.e. every insert, update, delete)
- Has to be completely successful or not at all
- Start the select statement with BEGIN TRAN and end it with COMMIT TRAN (ok) or ROLLBACK TRAN (cancel)
- So you can rollback if you make a mistake or commit if everything is okay to ahead with

- **set xact_abort on;** is automatic rollback if something goes wrong