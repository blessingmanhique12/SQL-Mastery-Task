# SQL Mastery Task: The University Database

## Your Mission
You are the new Database Administrator for the **University of Tech**.  
Your first task is to **create and manage the students table**.

---

## Step 1: Table Creation
Create the `students` table with the following columns:
- **student_id (Primary Key)**: A unique identifier for each student. It should auto-increment.  
- **name (VARCHAR)**: The student's first name.  
- **surname (VARCHAR)**: The student's last name.  
- **programme (VARCHAR)**: The degree programme the student is enrolled in (e.g., 'Data Science', 'Biotechnology').  
- **average (DECIMAL)**: The student's grade point average (GPA), which can be a value like 85.5.  
- **enrollment_date (DATE)**: The date the student enrolled at the university.  

**SQL Statement:**
```sql
CREATE TABLE students (
    student_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    surname VARCHAR(100),
    programme VARCHAR(100),
    average DECIMAL(5,2),
    enrollment_date DATE
);
````

---

## Step 2: Data Insertion

Now, populate the `students` table with the following data:

1. Emma Watson — Data Science — 2023-09-12 — 91.2
2. James Rodriguez — Biotechnology — 2022-08-25 — 78.5
3. Priya Patel — Robotics — 2023-09-20 — 98.0
4. Alex Turner — Data Science — 2021-09-05 — 84.3

**SQL Statements:**

```sql
INSERT INTO students (name, surname, programme, average, enrollment_date)
VALUES
('Emma', 'Watson', 'Data Science', 91.2, '2023-09-12'),
('James', 'Rodriguez', 'Biotechnology', 78.5, '2022-08-25'),
('Priya', 'Patel', 'Robotics', 98.0, '2023-09-20'),
('Alex', 'Turner', 'Data Science', 84.3, '2021-09-05');
```

---

## Step 3: Data Querying & Manipulation

### Question 1:

Retrieve a list of all students, showing only their **full name** (combine name and surname) and their **programme**.

```sql
SELECT CONCAT(name, ' ', surname) AS full_name, programme
FROM students;
```

### Question 2:

List the names and averages of all students with an average greater than 90, ordered from highest to lowest.

```sql
SELECT CONCAT(name, ' ', surname) AS full_name, average
FROM students
WHERE average > 90
ORDER BY average DESC;
```

### Question 3:

Update James Rodriguez’s average to 85.5.

```sql
UPDATE students
SET average = 85.5
WHERE name = 'James' AND surname = 'Rodriguez';
```

### Question 4:

Update Priya Patel’s programme to **Data Science**.

```sql
UPDATE students
SET programme = 'Data Science'
WHERE name = 'Priya' AND surname = 'Patel';
```

### Question 5:

Remove Alex Turner from the table.

```sql
DELETE FROM students
WHERE name = 'Alex' AND surname = 'Turner';
```

### Question 6:

Add a new student, **Lucas Kim**, who enrolled in **Cybersecurity** today with an average of **81.5**.

```sql
INSERT INTO students (name, surname, programme, average, enrollment_date)
VALUES ('Lucas', 'Kim', 'Cybersecurity', 81.5, CURRENT_DATE);
```

### Question 7:

Generate a report showing the **number of students in each programme**.

```sql
SELECT programme, COUNT(*) AS student_count
FROM students
GROUP BY programme;
```

---

## Step 4: Solution and Verification

After performing all operations, verify your results:

### View Final Table:

```sql
SELECT * FROM students;
```

### Verify Programme Distribution:

```sql
SELECT programme, COUNT(*) AS student_count
FROM students
GROUP BY programme;
```

If your SQL commands were executed correctly, you should now see:

* Emma Watson (Data Science, 91.2)
* James Rodriguez (Biotechnology, 85.5 after update)
* Priya Patel (Data Science, 98.0 after update)
* Lucas Kim (Cybersecurity, 81.5)

And your programme report should correctly show the count of students per programme.

```
