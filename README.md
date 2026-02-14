# AI DISCLAIMER

Queries:
1) "Insert into a table sql"
- This was used on google, and I got my response from Google search AI
- I couldn't remember the exact syntax
- Response:
```
Best Practice Syntax (Inserting into specific columns) 
It is generally recommended to explicitly specify the column names to make the SQL statement more readable and less error-prone, especially if the table structure changes. This also allows you to omit columns that have default values or are auto-generated (like IDENTITY columns). 
sql

INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

```
2) "give me separate examples of a sqlite join of two tables, as well as a group of two tables"
- I couldn't remember syntax in SQL
- Gemini 3 fast (web)
- Response (the bit I used):
```
SELECT Employees.Name, Departments.DeptName
FROM Employees
INNER JOIN Departments ON Employees.DeptID = Departments.DeptID;
```
- Response 2:
```
SELECT 
    Departments.DeptName, 
    COUNT(Employees.EmployeeID) AS TotalStaff
FROM Departments
LEFT JOIN Employees ON Departments.DeptID = Employees.DeptID
GROUP BY Departments.DeptName;
```

## 1) 
CREATE TABLE "MusicVideo" (
	"TrackID"	INTEGER,
	"VideoDirector"	TEXT,
	PRIMARY KEY("TrackID"),
	FOREIGN KEY("TrackID") REFERENCES "tracks"("TrackID")
);

## 2) 
INSERT INTO MusicVideo (TrackId, VideoDirector) VALUES
    (1, 'a'),
    (2, 'b'),
    (3, 'c'),
    (4, 'd'),
    (5, 'e'),
    (6, 'f'),
    (7, 'g'),
    (8, 'h'),
    (9, 'i'),
    (10, 'j')

## 3)
INSERT INTO MusicVideo (TrackId, VideoDirector)
SELECT TrackId, NULL
FROM tracks
WHERE Name = 'Voodoo';

## 4)
SELECT TrackId
FROM tracks 
WHERE Name LIKE '%á%' 
   OR Name LIKE '%é%' 
   OR Name LIKE '%í%' 
   OR Name LIKE '%ó%' 
   OR Name LIKE '%ú%';

## 5)
SELECT customers.CustomerId, customers.LastName, invoices.InvoiceId, invoices.Total
FROM customers
INNER JOIN invoices ON customers.CustomerId = invoices.CustomerId;

## 6) 
SELECT
    customers.CustomerId,
    customers.LastName,
    COUNT(invoices.InvoiceId) AS InvoiceCount
FROM customers
LEFT JOIN invoices ON customers.CustomerId = invoices.CustomerId
GROUP BY customers.CustomerId, customers.LastName;
