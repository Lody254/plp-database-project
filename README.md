# plp-database-project
 README.md

 # 📚 Library Management System (MySQL)

## 📝 Description
This project implements a full relational database for managing a library system. It includes tables for members, books, authors, loans, and categories, as well as relationships like many-to-many (books & authors) and one-to-many (categories to books, members to loans).

## 🚀 How to Run / Setup
1. Make sure you have MySQL installed (e.g., MySQL Workbench or XAMPP).
2. Clone this repository:
   ```bash
   git clone https://github.com/your-username/library-management-db.git
SQL

---

## 📂 `library_management.sql` (with comments)

Here’s the file content with SQL comments:

```sql
-- Library Management System Database
-- Author: [Your Name]
-- Description: This script creates a complete relational DB with constraints and relationships.

-- Members table
CREATE TABLE Members (
    member_id INT AUTO_INCREMENT PRIMARY KEY,
    full_name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone VARCHAR(20),
    registration_date DATE NOT NULL
);

-- Authors table
CREATE TABLE Authors (
    author_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    birth_year INT
);

-- Categories table
CREATE TABLE Categories (
    category_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL UNIQUE
);

-- Books table
CREATE TABLE Books (
    book_id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(200) NOT NULL,
    category_id INT,
    published_year INT,
    isbn VARCHAR(20) UNIQUE,
    copies_available INT NOT NULL DEFAULT 0,
    FOREIGN KEY (category_id) REFERENCES Categories(category_id)
);

-- Book_Author table to model many-to-many relationship
CREATE TABLE Book_Author (
    book_id INT,
    author_id INT,
    PRIMARY KEY (book_id, author_id),
    FOREIGN KEY (book_id) REFERENCES Books(book_id),
    FOREIGN KEY (author_id) REFERENCES Authors(author_id)
);

-- Loans table to track book borrowing
CREATE TABLE Loans (
    loan_id INT AUTO_INCREMENT PRIMARY KEY,
    member_id INT,
    book_id INT,
    loan_date DATE NOT NULL,
    return_date DATE,
    FOREIGN KEY (member_id) REFERENCES Members(member_id),
    FOREIGN KEY (book_id) REFERENCES Books(book_id)
);

bash

git init
git add .
git commit -m "Initial commit: Library Management System DB"
git remote add origin https://github.com/your-username/library-management-db.git
git push -u origin master





