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
3. Create a table named Customers in the QuantigrationUpdates database.
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

---
### Part 2 – Data Import

---
### Part 3 – Data Queries & Updates

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















