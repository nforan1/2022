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

- Even though we type Select > From>Where>Order By..., SQL server runs From > Where select > Orderd by...This means that we cannot use an alias in the WHERE clause (because it is only created in the SELECT clause)

---


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

This only shows each country once (no duplicates)

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

## Creating Table- Query
    Create table dbo.workers(
        WorkerID int NOT NULL primary key identity (1,1)
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