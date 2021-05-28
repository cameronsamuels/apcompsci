# students.sql - SQLite Database

```sql
CREATE DATABASE IF NOT EXISTS student

-- -----
-- Table Structure
-- -----

CREATE TABLE students (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  student_id CHAR(9),
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  email_address VARCHAR(250),
  notes TEXT(1000)
);

CREATE TABLE courses (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  course_id VARCHAR(10)
    CHECK (length(course_id) >= 2),
  name VARCHAR(100),
  notes TEXT(1000)
);

CREATE TABLE grades (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  student_id INTEGER,
  course_id INTEGER,
  grade_type_id INTEGER,
  score DECIMAL(5,2),
  notes TEXT(1000)
);
  
CREATE TABLE grade_types (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name VARCHAR(100),
  weight DECIMAL(5,2)
    CHECK (weight <= 100.00)
);

-- ------
-- INSERT STUDENTS
-- ------

INSERT INTO students (student_id, first_name, last_name, email_address)
  VALUES
    ('K1928374', 'Chaya', 'Sanders', 'chayasanders@google.com'),
    ('K6574839', 'Joseya', 'Donem', 'joseya.donem@google.com')
;
    
INSERT INTO students (student_id, first_name, last_name, email_address, notes)
  VALUES
    ('K5647382', 'Kamala', 'Donem', 'donem.kamala@google.com', 'Straight A student'),
    ('K9182736', 'Amaya', 'Sanders', 'amayasanders@google.com', 'Faied to adhere to COVID precautions'),
    ('K8765341', 'Philla', 'Lim', 'phillim@google.com', 'Allergic to mustard')
;

-- -----
-- INSERT COURSES
-- -----

INSERT INTO courses (course_id, name)
  VALUES ('APCHEM', 'AP Chemistry');

-- -----
-- INSERT GRADE TYPES
-- -----

INSERT INTO grade_types (name, weight)
  VALUES
    ('Major', 60.00),
    ('Minor', 30.00),
    ('Other', 10.00)
;

-- -----
-- INSERT GRADES
-- -----

INSERT INTO grades (student_id, course_id, grade_type_id, score, notes)
  VALUES
    -- Gas Laws Test
    (1, 1, 1, 90.00, NULL),
    (2, 1, 1, 80.00, NULL),
    (3, 1, 1, 105.00, '5 points extra credit applied'),
    (4, 1, 1, 70.00, 'Score after retest'),
    (5, 1, 1, 80.00, '5 points extra credit applied'),
    
    -- Gas Laws Lab
    (1, 1, 2, 100.00, NULL),
    (2, 1, 2, 75.00, 'Unable to complete last section'),
    (3, 1, 2, 100.00, NULL),
    (4, 1, 2, 65.00, 'Did first section incorrectly; Unable to complete last section'),
    (5, 1, 2, 90.00, 'Did last section icorrectly'),
    
    -- Gas Laws Homework Worksheet
    (1, 1, 3, 100.00, NULL),
    (2, 1, 3, 50.00, 'Only half was completed'),
    (3, 1, 3, 100.00, NULL),
    (4, 1, 3, 0.00, 'Not turned in'),
    (5, 1, 3, 90.00, 'Submitted late'),
    
    -- Gas Laws Classwork
    (1, 1, 3, 90.00, 'Unable to complete last section'),
    (2, 1, 3, 90.00, 'Unable to complete last section'),
    (3, 1, 3, 50.00, 'Only half was completed'),
    (4, 1, 3, 100.00, 'Absent, submitted late for full credit'),
    (5, 1, 3, 100.00, NULL)
;
```
