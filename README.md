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

- There were a total of 505 orders placed by customers in Framingham, Massachusetts. This query determines the total number of orders by performing an inner join between the customer table and the orders table.



---

## 🎯 Learning Outcomes
- Schema design  
- Data import and transformation  
- SQL querying (SELECT, INSERT, UPDATE, DELETE)  
- Data export  
- Relational database management  

---

## 🛠 Technologies Used
- **MySQL**
- **CSV Data Files**















