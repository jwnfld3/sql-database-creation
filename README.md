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

### Step 1: Create the Database

```sql
CREATE DATABASE ShopEZ;
```

**Explanation**:  
This command initializes a new SQL database named `ShopEZ`, which will act as the container for all tables, data, and future operations.

---

### Step 2: Switch to the New Database

```sql
USE ShopEZ;
```

**Explanation**:  
Before creating tables, the session needs to explicitly reference the correct database. This ensures all following operations are executed inside the `ShopEZ` environment.

---

### Step 3: Create the `Customers` Table

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY IDENTITY(1,1),
    FirstName NVARCHAR(50),
    LastName NVARCHAR(50),
    Email NVARCHAR(100),
    JoinDate DATE
);
```

**Explanation**:  
This table will store customer information. `CustomerID` is an auto-incrementing primary key. `FirstName`, `LastName`, and `Email` are text fields, while `JoinDate` records when the customer was added to the system.

---

### Step 4: Create the `Orders` Table

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY IDENTITY(1,1),
    CustomerID INT,
    OrderDate DATE,
    TotalAmount DECIMAL(10,2),
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

**Explanation**:  
The `Orders` table captures each transaction. `CustomerID` links each order to a customer in the `Customers` table, enforcing a one-to-many relationship via a foreign key. `TotalAmount` is a decimal value supporting two decimal places for currency.

---

## Conclusion

By completing this lab, a functional SQL database structure has been created, capable of storing customer and order data. This structure is foundational for performing business queries, customer management, and financial reporting in future labs or development stages.
