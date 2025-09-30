# MySQL DB Project

## 📌 Overview
This project was completed in Codio as part of my university Database course (DAD-202) and focuses on creating and managing a **MySQL** database.  
It demonstrates database design, data loading, and SQL queries for data analysis and management.

---

## 🗂 Project Structure

### Part 1 – Database Creation
- Create a schema: **QuantigrationUpdates**
- Define tables: **Customers**, **Orders**, and **RMA**

### Part 2 – Data Import
- Load data from CSV files into the created tables

### Part 3 – Data Queries & Updates
- Query customer and order data (e.g., filter by city/state)
- Insert new customer records  
- Update and delete records in **RMA** and **Orders**  
- Rename all instances of *Customer* to *Collaborator*  
- Export query results to a `.csv` file  
---
### Part 1 – Database Creation

1.	In Codio navigate to your online integrated development environment (IDE).
* chmod +x change_perm.sh
* ./change_perm.sh
* mysql

<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/2ba1ea0e-12c1-47d0-8de7-e59ba39dcce0" style="max-width: 200px; width: 60%; height: auto;" />
  </div>
  
<br></br>
2. Create a database schema called QuantigrationUpdates. List out the database name.
* CREATE DATABASE QuantigrationUpdates;
* SHOW DATABASES;
* USE QuantigrationUpdates;
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/e8ea70b3-f51a-4fa5-a716-a507f39c9f7c" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
3. Create a table named **Customers** in the QuantigrationUpdates database.
* CREATE TABLE Customers (
  * CustomerID INT,
  * FirstName VARCHAR(25),
  * LastName VARCHAR(25),
  * Street VARCHAR(50),
  * City VARCHAR(50),
  * State VARCHAR(25),
  * ZipCode VARCHAR(10),
  * Telephone VARCHAR(15),
  * PRIMARY KEY (CustomerID)
  * );
* DESCRIBE Customers;
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/8db03915-4ee7-4df0-9e0b-004b8bc9ae2f" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
4. Create a table named **Orders** in the QuantigrationUpdates database.
* CREATE TABLE Orders (
  * OrderID INT,
  * CustomerID INT,
  * SKU VARCHAR(20),
  * Description VARCHAR(50),
  * PRIMARY KEY (OrderID),
  * FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
  * );
* DESCRIBE Orders;
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/04149002-68c5-47d7-a1e3-40baabc2e5bb" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
5. Create a table named **RMA** in the QuantigrationUpdates database.
* CREATE TABLE RMA (
  * RMAID INT,
  * OrderID INT,
  * Step VARCHAR(50),
  * Status VARCHAR(15),
  * Reason VARCHAR(15),
  * PRIMARY KEY (RMAID),
  * FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
  * );
* DESCRIBE RMA;
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/ab9747cf-029d-4a11-a5cf-f1e061f95ffb" style="max-width: 200px; width: 60%; height: auto;" />
  </div>
  
---
### Part 2 – Importing Data

1. Import data from the CSV files into the Customers, Orders, and RMA tables in the QuantigrationUpdates database.
* LOAD DATA INFILE (/PATH)
  * INTO TABLE (Customers/Orders/RMA)
  * FIELDS TERMINATED BY ','
  * LINES TERMINATED BY '\n'
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/7e156c25-b79a-42e1-9ee3-9b939713f8e1" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

---
### Part 3 – Data Queries & Updates

1. Write an SQL query that returns the count of orders for customers located only in the city of Framingham, Massachusetts.
* SELECT COUNT(*)
  * FROM Customers
  * INNER JOIN Orders ON Orders.CustomerID = Customers.CustomerID
  * WHERE City = 'Framingham' AND State = 'Massachusetts';
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/469a33d0-4976-455d-b9e7-87907613bc4e" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
There were a total of 505 orders placed by customers in Framingham, Massachusetts. This query determines the total number of orders by performing an inner join between the customer table and the orders table.

<br></br>
2. Write an SQL query to select all of the Customers located in the state of Massachusetts. Use a WHERE clause to limit the number of records in the Customers table to only those who are located in Massachusetts.
* SELECT *
  * FROM Customers
  * WHERE State = 'Massachusetts';
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/8ed191cc-efdb-44e9-b1fa-d839c5bba221" style="max-width: 200px; width: 60%; height: auto;" />
    <img src="https://github.com/user-attachments/assets/957a24b3-eba9-49ea-bf26-4fc5ee99cdb0" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
In Massachusetts, there are 982 customers.

<br></br>
3. Write a SQL query to insert four new records into the Orders and Customers tables using the following data:

### Orders Table

| OrderID   | CustomerID | SKU        | Description                                               |
|-----------|------------|------------|-----------------------------------------------------------|
| 1204305   | 100004     | ADV-24-10C | Advanced Switch 10GigE Copper 24 port                     |
| 1204306   | 100005     | ADV-48-10F | Advanced Switch 10 GigE Copper/Fiber 44 port copper 4 port fiber |
| 1204307   | 100006     | ENT-24-10F | Enterprise Switch 10GigE SFP+ 24 Port                     |
| 1204308   | 100007     | ENT-48-10F | Enterprise Switch 10GigE SFP+ 48 port                     |

* INSERT INTO Orders VALUES (1204305, 100004, 'ADV-24-10C', 'Advanced Switch 10GigE Copper 24 port'),
  * (1204306, 100005, 'ADV-48-10F', 'Advanced Switch 10 GigE Copper/Fiber 44 port copper 4 port fiber'),
  * (1204307, 100006, 'ENT-24-10F', 'Enterprise Switch 10GigE SFP+ 24 Port'),
  * (1204308, 100007, 'ENT-48-10F', 'Enterprise Switch 10GigE SFP+ 48 port');
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/d821720e-8dc7-43ba-90e6-4a607e73fe4e" style="max-width: 200px; width: 60%; height: auto;" />
  </div>


### Customers Table

| CustomerID | FirstName | LastName   | StreetAddress           | City       | State | ZipCode | Telephone     |
|------------|-----------|------------|------------------------|------------|-------|---------|---------------|
| 100004     | Luke      | Skywalker  | 15 Maiden Lane         | New York   | NY    | 10222   | 212-555-1234  |
| 100005     | Winston   | Smith      | 123 Sycamore Street    | Greensboro | NC    | 27401   | 919-555-6623  |
| 100006     | MaryAnne  | Jenkins    | 1 Coconut Way          | Jupiter    | FL    | 33458   | 321-555-8907  |
| 100007     | Janet     | Williams   | 55 Redondo Beach Blvd  | Torrence   | CA    | 90501   | 310-555-5678  |

* INSERT INTO Customers VALUES(100004, 'Luke', 'Skywalker', '15 Maiden Lane', 'New York', 'NY', '10222', '212-555-1234'),
  * (100005, 'Winston', 'Smith', '123 Sycamore Street', 'Greensboro', 'NC', '27401', '919-555-6623'),
  * (100006, 'MaryAnne', 'Jenkins', '1 Coconut Way', 'Jupiter', 'FL', '33458', '321-555-8907'),
  * (100007, 'Janet', 'Williams', '55 Redondo Beach Blvd', 'Torrence', 'CA', '90501', '310-555-5678');
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/fa7e0004-0f40-456d-a646-b64d9e32b6cf" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
4. In the Customers table, perform a query to count all records where the city is Woonsocket, Rhode Island.
* SELECT COUNT(*)
  * FROM Customers
  * WHERE CITY = 'Woonsocket' AND State = 'Rhode Island';
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/d97537d5-a1c1-4c34-94c5-112bff1e4deb" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
Woonsocket, Rhode Island has a total of 7 customer records.

<br></br>
5. In the RMA database, update a customer’s records. Write an SQL statement to select the current fields of status and step for the record in the RMA table with an orderID value of “5175.”
* SELECT Status, Step
  * FROM RMA
  * WHERE OrderID = 5175;
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/141dfce3-b124-4595-a4b5-c9786e7cd3a2" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
orderID 5175 is currently in a Pending status, and step is awaiting customer documentation.

<br></br>
6. Write an SQL statement to update the status and step for the OrderID, 5175 to status = “Complete” and step = “Credit Customer Account”.
* UPDATE RMA
  * SET Status = 'Complete', Step = 'Credit Customer Account'
  * WHERE OrderID = 5175;
<br></br>
* SELECT Status, Step
  * FROM RMA
  * WHERE OrderID = 5175;
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/92a7387f-e326-40cc-becf-b2a8821b1ccc" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
OrderID 5175 has been updated with a new Status and Step.

<br></br>
7. Delete RMA records. Write an SQL statement to delete all records with a reason of “Rejected.”
* DELETE FROM RMA
  * WHERE Reason LIKE '%Rejected%';
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/300590ac-7d93-4dc7-b346-3a550ae8ad51" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
In total, 596 records were deleted from the database.

<br></br>
8. Update your existing tables Rename all instances of “Customer” to “Collaborator”.
* CREATE VIEW Collaborator AS 
  * SELECT CustomerID AS CollaboratorID,
  * FirstName,
  * LastName,
  * Street,
  * City,
  * State,
  * ZipCode,
  * Telephone
  * FROM Customers;
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/024cf97d-d6c8-449e-a379-75dfcf60e466" style="max-width: 200px; width: 60%; height: auto;" />
  </div>
  
<br></br>
* DESCRIBE Collaborator;
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/a4feaf22-b0df-44df-98a0-76f8af715692" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

<br></br>
9. Write an SQL statement to list the contents of the Orders table and send the output to a CSV file titled orders_updated.csv
* SELECT *
  * FROM Orders
  * INTO OUTFILE '/PATH/orders_updated.csv'
  * FIELDS TERMINATED BY ','
  * LINES TERMINATED BY '\r\n';
<div style="margin-bottom: 30px;"; justify-content: center; gap: 5px; flex-wrap: nowrap;">
    <img src="https://github.com/user-attachments/assets/eb9d46e4-474e-42c7-a1aa-5bd6aa97d87d" style="max-width: 200px; width: 60%; height: auto;" />
  </div>

---

## Learning Outcomes
- Schema design  
- Data import and transformation  
- SQL querying (SELECT, INSERT, UPDATE, DELETE)  
- Data export  
- Relational database management  
















