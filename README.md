# SQL Lab 1: Create a Customer Database

## Overview
This lab simulates the initial setup of a customer and order tracking system for a small e-commerce company. It focuses on designing a basic relational database using SQL. Two tables — `Customers` and `Orders` — will be created to support customer management and order processing.

## Who / What / Where / When / Why

- **Who**: A junior database administrator working for a startup online retailer.
- **What**: Create a SQL Server database named `ShopEZ`, including `Customers` and `Orders` tables with a relational structure.
- **Where**: Executed in SQL Server Management Studio (SSMS), Azure Data Studio, or a compatible SQL environment.
- **When**: During the system's initial setup phase before launch.
- **Why**: To implement a structured data model that supports customer tracking, order history, and future analytics.

---

## Steps

### Step 1: Launch SQL Server Management Studio (SSMS)

- Open SSMS from the Windows Start Menu.
- Wait for the application to load.

**Explanation**: SSMS is the primary tool used to interact with SQL Server environments. It provides an interface to create and manage databases.

![image](https://github.com/user-attachments/assets/5cba38ab-3af8-433e-bb56-826b49d1a892)

---

### Step 2: Connect to a SQL Server Instance

- In Object Explorer, click the **Connect** button.
- Select **Database Engine**.
- For **Server Name**, enter `localhost`, `.`, or `(local)` if SQL Server is installed locally.
- Choose **Windows Authentication** (default).
- Click **Connect**.

**Explanation**: This step connects to the local SQL Server instance, making it possible to issue SQL commands.

![image](https://github.com/user-attachments/assets/1f303886-29d8-4c1b-8662-7ac0f9184e4d)

---

### Step 3: Open a New Query Window

- Click on **New Query** in the top toolbar.
- A new blank query editor will open.

**Explanation**: This window is where SQL statements are written and executed.

![image](https://github.com/user-attachments/assets/587dc57f-3c79-40b9-ae74-7f4839ae50c7)

---

### Step 4: Create the ShopEZ Database

```sql
CREATE DATABASE ShopEZ;
```
- Paste the command into the query window.
- Click **Execute** (or press F5).

**Explanation**: This command initializes a new database named `ShopEZ`, which will store all the related tables.

![image](https://github.com/user-attachments/assets/56d4c2df-bd85-406c-93b6-c853fd20b3fd)

---

### Step 5: Switch to the ShopEZ Database

```sql
USE ShopEZ;
```
- Paste the command below the previous one or in a new query window.
- Click **Execute**.

**Explanation**: This command sets `ShopEZ` as the current working database so that all future actions apply to it.

![image](https://github.com/user-attachments/assets/1685aa37-650c-47fa-a50e-b2120d6ac3ba)

---

### Step 6: Create the Customers Table

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY IDENTITY(1,1),
    FirstName NVARCHAR(50),
    LastName NVARCHAR(50),
    Email NVARCHAR(100),
    JoinDate DATE
);
```
- Paste into the query editor.
- Click **Execute**.

**Explanation**: This creates a table to store customer details. `CustomerID` is auto-incremented and used as the primary key.

![image](https://github.com/user-attachments/assets/b07ebbff-66bf-4564-9dec-66a6cb2a1324)

## Line-by-Line Explanation

### `CREATE TABLE Customers (`
Starts the creation of a new table named `Customers`.

---

### `CustomerID INT PRIMARY KEY IDENTITY(1,1),`
- **CustomerID**: Column name that uniquely identifies each customer.  
- **INT**: Data type for whole numbers.  
- **PRIMARY KEY**: Ensures uniqueness and non-null values for this column.  
- **IDENTITY(1,1)**: Automatically generates incremental values starting at 1 and increasing by 1 for each new row.

---

### `FirstName NVARCHAR(50),`
- Stores the customer's first name.  
- `NVARCHAR(50)` allows up to 50 Unicode characters for multilingual support.

---

### `LastName NVARCHAR(50),`
- Stores the customer's last name.  
- Also uses `NVARCHAR(50)` to support international character sets.

---

### `Email NVARCHAR(100),`
- Holds the customer's email address.  
- `NVARCHAR(100)` allows for longer email formats, up to 100 characters.

---

### `JoinDate DATE`
- Tracks the date the customer joined.  
- `DATE` stores only the date portion (e.g., `2025-05-01`), with no time.

---

### `);`
Ends the `CREATE TABLE` command.
---

### Step 7: Create the Orders Table

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY IDENTITY(1,1),
    CustomerID INT,
    OrderDate DATE,
    TotalAmount DECIMAL(10,2),
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```
- Paste into the query editor.
- Click **Execute**.

**Explanation**: This table stores order data and references `CustomerID` from the `Customers` table to maintain relational integrity.

---

## Conclusion

This lab walked through connecting to SQL Server via SSMS, creating a database, and designing two foundational tables. The structure supports essential operations like storing customer profiles and tracking their orders, which are key components of any transactional business application.
