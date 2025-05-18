
# 📘 PostgreSQL Students Table Management

This repository contains SQL scripts to demonstrate basic and advanced usage of PostgreSQL for managing a `students` table. It includes table creation, insertion, querying, filtering, scalar and aggregate functions, pagination, and data manipulation operations like update and delete.

## 🏗️ Table Structure

```sql
CREATE TABLE students (
    student_id SERIAL PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT,
    grade CHAR(2),
    course VARCHAR(70),
    email VARCHAR(100),
    dob DATE,
    blood_group VARCHAR(5),
    country VARCHAR(50)
);
```

## 📥 Insert Sample Data

Bulk insert of multiple student records:

```sql
INSERT INTO students (first_name, last_name, age, grade, course, email, dob, blood_group, country) VALUES
('Abu', 'Rayhan', 22, 'A+', 'English', 'aburayhan.bpi@gmail.com', '2003-10-17', 'B+', 'Bangladesh'),
('Hasib', 'Hossain', 23, 'B+', 'Mathematics', 'hasib.hossain@gmail.com', '2002-06-05', 'A-', 'India'),
...
('Tusar', 'Hossain', 25, 'A+', 'Statistics', NULL, '2000-07-21', 'O+', 'India');
```

## 🧹 Table Management

- **Drop table:**  
  ```sql
  DROP TABLE students;
  ```

- **Truncate table (delete all rows):**  
  ```sql
  TRUNCATE TABLE students;
  ```

## 📄 Basic Queries

- **Select all students:**  
  ```sql
  SELECT * FROM students;
  ```

- **Select specific columns:**  
  ```sql
  SELECT email, age, country, blood_group FROM students;
  ```

- **Use aliasing:**  
  ```sql
  SELECT email AS "student email" FROM students;
  ```

## 🔍 Sorting and Filtering

- **Sort by age ascending:**  
  ```sql
  SELECT * FROM students ORDER BY age ASC;
  ```

- **Distinct values:**  
  ```sql
  SELECT DISTINCT country FROM students;
  SELECT DISTINCT blood_group FROM students;
  ```

### 🎯 Conditional Filtering Examples

- Students from the USA:
  ```sql
  SELECT * FROM students WHERE country = 'USA';
  ```

- Students with grade 'A+' or enrolled in 'Physics':
  ```sql
  SELECT * FROM students WHERE grade = 'A+' OR course = 'Physics';
  ```

- Students with blood group A+:
  ```sql
  SELECT * FROM students WHERE blood_group = 'A+';
  ```

- From USA or Australia and age is 20:
  ```sql
  SELECT * FROM students WHERE (country = 'USA' OR country = 'Australia') AND age = 20;
  ```

- Grade A or B in Math or Physics:
  ```sql
  SELECT * FROM students WHERE (grade = 'A' OR grade = 'B') AND (course = 'Math' OR course = 'Physics');
  ```

- Students older than 20:
  ```sql
  SELECT * FROM students WHERE age <> 20;
  ```

## 🔡 Scalar Functions

- **Convert names to uppercase:**  
  ```sql
  SELECT UPPER(first_name) AS first_name_upper, * FROM students;
  ```

- **Concatenate full name:**  
  ```sql
  SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM students;
  ```

## 📊 Aggregate Functions

```sql
SELECT AVG(age) FROM students;
SELECT MAX(age) FROM students;
SELECT MIN(age) FROM students;
SELECT SUM(age) FROM students;
SELECT COUNT(*) FROM students;
SELECT MAX(LENGTH(first_name)) FROM students;
```

## ❗NULL Handling

- **Check for NULL emails:**  
  ```sql
  SELECT * FROM students WHERE email IS NULL;
  ```

- **Provide default text for NULL emails:**  
  ```sql
  SELECT COALESCE(email, 'Email not provided') AS Email, blood_group, country FROM students;
  ```

## ✅ IN, NOT IN, BETWEEN, LIKE

- **Use IN and NOT IN:**
  ```sql
  SELECT * FROM students WHERE country IN ('USA', 'Canada', 'Malaysia');
  SELECT * FROM students WHERE country NOT IN ('USA', 'Canada', 'Malaysia');
  ```

- **Use BETWEEN:**
  ```sql
  SELECT * FROM students WHERE age BETWEEN 18 AND 20;
  SELECT * FROM students WHERE dob BETWEEN '2000-01-01' AND '2005-01-01' ORDER BY dob;
  ```

- **Use LIKE and ILIKE (case-insensitive):**
  ```sql
  SELECT * FROM students WHERE first_name LIKE 'A%';
  SELECT * FROM students WHERE first_name LIKE '%a';
  SELECT * FROM students WHERE first_name ILIKE 'a%';
  ```

## 📚 Pagination

- **Limit rows:**
  ```sql
  SELECT * FROM students LIMIT 4;
  ```

- **Pagination with offset:**
  ```sql
  SELECT * FROM students LIMIT 5 OFFSET 0; -- Page 1
  SELECT * FROM students LIMIT 5 OFFSET 5; -- Page 2
  SELECT * FROM students LIMIT 5 OFFSET 10; -- Page 3
  ```

## 🧾 Data Manipulation

### 🔄 Update Data

```sql
UPDATE students
SET email = 'default@gmail.com', age = 29
WHERE student_id = 11;
```

### ❌ Delete Specific Records

```sql
DELETE FROM students
WHERE grade = 'C' AND country = 'Malaysia';
```

---

## 📌 Notes

- Some student records have `NULL` values for email.
- Queries demonstrate both filtering and aggregation use cases.
- Designed for learning PostgreSQL fundamentals.

---

## 📎 Author

**Abu Rayhan**  
Junior Frontend Developer | MERN Stack Developer  
Email: aburayhan.bpi@gmail.com  
Location: Bogura, Bangladesh
