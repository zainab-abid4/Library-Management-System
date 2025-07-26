**Project Title:** Library Management System

##  PROJECT OVERVIEW 

This project demonstrates the implementation of a Library Management System using SQL. It includes creating and managing tables, performing CRUD operations, and executing advanced SQL queries. The goal is to showcase skills in database design, manipulation, and querying.

##  OBJECTIVES 

- **Set up the Library Management System Database:**  
  Create and populate the database with tables for branches, employees, members, books, issued status, and return status.

- **CRUD Operations:**  
  Perform Create, Read, Update, and Delete operations on the data.

- **CTAS Operations:**  
  Utilize CTAS to create new tables based on query results.

- **Advanced SQL Queries:**  
  Develop complex queries to analyze and retrieve specific data.

  
##  LIBRARY DATABASE 
![Alt Text](https://github.com/zainab-abid4/Library-Management-System/blob/5ceadc37fdc34c86ba42ca30669ba70ec0d1b64d/Library%20Database.PNG)

```sql
CREATE DATABASE library;

USE library;

DROP TABLE IF EXISTS employees;
CREATE TABLE employees
(
            emp_id VARCHAR(10) PRIMARY KEY,
            emp_name VARCHAR(30),
            position VARCHAR(30),
            salary DECIMAL(10,2),
            branch_id VARCHAR(10),
);


DROP TABLE IF EXISTS members;
CREATE TABLE members
(
            member_id VARCHAR(10) PRIMARY KEY,
            member_name VARCHAR(30),
            member_address VARCHAR(30),
            reg_date DATE
);


DROP TABLE IF EXISTS books;
CREATE TABLE books
(
            isbn VARCHAR(50) PRIMARY KEY,
            book_title VARCHAR(80),
            category VARCHAR(30),
            rental_price DECIMAL(10,2),
            status VARCHAR(10),
            author VARCHAR(30),
            publisher VARCHAR(30)
);


DROP TABLE IF EXISTS issued_status;
CREATE TABLE issued_status
(
            issued_id VARCHAR(10) PRIMARY KEY,
            issued_member_id VARCHAR(30),
            issued_book_name VARCHAR(80),
            issued_date DATE,
            issued_book_isbn VARCHAR(50),
            issued_emp_id VARCHAR(10),
            FOREIGN KEY (issued_member_id) REFERENCES members(member_id),
            FOREIGN KEY (issued_emp_id) REFERENCES employees(emp_id),
            FOREIGN KEY (issued_book_isbn) REFERENCES books(isbn) 
);


DROP TABLE IF EXISTS return_status;
CREATE TABLE return_status
(
            return_id VARCHAR(10) PRIMARY KEY,
            issued_id VARCHAR(30),
            return_book_name VARCHAR(80),
            return_date DATE,
            return_book_isbn VARCHAR(50),
            FOREIGN KEY (return_book_isbn) REFERENCES books(isbn)
);
```
##  CONCLUSIONS 
The system effectively handles core library functions, offering a reliable and efficient solution for managing resources. It serves as a strong foundation for future enhancements and real- world application in academic or public libraries. 

