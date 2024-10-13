---
layout: post
title: UoE - Deciphering Big Data July 2024 - Data Build Task
subtitle: 
- Critically analyse data wrangling problems and determine appropriate methodologies, tools, and techniques (involving preparing, cleaning, exploring, creating, optimising and evaluating big data) to solve them. 
- Design, develop and evaluate solutions for processing datasets and solving complex problems in various environments using relevant programming paradigms.
- Systematically develop and implement the skills required to be effective member of a development team in a virtual professional environment, adopting real life perspectives on team roles and organisation.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Data Build Task
---

### Create the Database and Tables

Implement the normalized tables in a database system (such as MySQL, PostgreSQL, or SQLite). Use the structure derived from the Third Normal Form (3NF) created earlier. Below is how each table can be defined with primary and foreign keys:


    CREATE DATABASE SchoolDB;
    USE SchoolDB;

    -- Students Table
      CREATE TABLE Students (
        StudentID INT PRIMARY KEY,
        StudentName VARCHAR(100),
        DateOfBirth DATE
      );


    -- Courses Table
      CREATE TABLE Courses (
        CourseID INT PRIMARY KEY,
        CourseName VARCHAR(100)
      );

    -- Teachers Table
      CREATE TABLE Teachers (
        TeacherID INT PRIMARY KEY,
        TeacherName VARCHAR(100)
      );

    -- Exam Boards Table
      CREATE TABLE ExamBoards (
        BoardID INT PRIMARY KEY,
        BoardName VARCHAR(100)
      );

    -- StudentCourses Table (many-to-many relationship between students and courses)
      CREATE TABLE StudentCourses (
        StudentID INT,
        CourseID INT,
        TeacherID INT,
        BoardID INT,
        ExamScore INT,
        SupportNeeded BOOLEAN,
        
        PRIMARY KEY (StudentID, CourseID),
        FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
        FOREIGN KEY (CourseID) REFERENCES Courses(CourseID),
        FOREIGN KEY (TeacherID) REFERENCES Teachers(TeacherID),
        FOREIGN KEY (BoardID) REFERENCES ExamBoards(BoardID)
      );

### Insert Data

Once the tables are created, data from the original unnormalized form can be inserted into the normalized tables.

    -- Insert data into Students
      INSERT INTO Students (StudentID, StudentName, DateOfBirth)
      VALUES 
        (1001, 'Bob Baker', '2001-08-25'),
        (1002, 'Sally Davies', '1999-10-02'),
        (1003, 'Mark Hanmill', '1995-06-05'),
        (1004, 'Anas Ali', '1980-08-03'),
        (1005, 'Cheuk Yin', '2002-05-01');

    -- Insert data into Courses
      INSERT INTO Courses (CourseID, CourseName)
      VALUES 
        (1, 'Computer Science'),
        (2, 'Maths'),
        (3, 'Physics'),
        (4, 'Biology'),
        (5, 'Music');

    -- Insert data into Teachers
      INSERT INTO Teachers (TeacherID, TeacherName)
      VALUES 
        (1, 'Mr Jones'),
        (2, 'Ms Parker'),
        (3, 'Mr Peters'),
        (4, 'Mrs Patel'),
        (5, 'Ms Daniels');

    -- Insert data into ExamBoards
      INSERT INTO ExamBoards (BoardID, BoardName)
      VALUES 
        (1, 'BCS'),
        (2, 'EdExcel'),
        (3, 'OCR'),
        (4, 'AQA'),
        (5, 'WJEC');

    -- Insert data into StudentCourses (linking students to courses, teachers, and exam boards)
      INSERT INTO StudentCourses (StudentID, CourseID, TeacherID, BoardID, ExamScore, SupportNeeded)
      VALUES 
        (1001, 1, 1, 1, 78, FALSE),
        (1001, 2, 2, 2, 78, FALSE),
        (1001, 3, 3, 3, 78, FALSE),
        (1002, 2, 2, 4, 55, TRUE),
        (1002, 4, 4, 5, 55, TRUE),
        (1002, 5, 5, 4, 55, TRUE),
        (1003, 1, 1, 1, 90, FALSE),
        (1003, 2, 2, 2, 90, FALSE),
        (1003, 3, 3, 3, 90, FALSE);

### Test the Database

To ensure referential integrity, run queries to:

Prevent data from being inserted into a child table (e.g., StudentCourses) if the foreign key does not exist in the parent table (e.g., Students, Courses).
Ensure that deleting a record in a parent table (e.g., Students) cascades or restricts deletion in related tables.

    -- Check if a student can be deleted
      DELETE FROM Students WHERE StudentID = 1001;

    -- Try inserting a record with non-existent foreign keys
      INSERT INTO StudentCourses (StudentID, CourseID, TeacherID, BoardID, ExamScore, SupportNeeded)
      VALUES (9999, 1, 1, 1, 85, FALSE); -- Should fail, as student 9999 does not exist


---
## Individual Reflecion
---

### Reflection

The Data Build Task provided an invaluable hands-on experience in transforming a normalized database design into an operational system. This task allowed me to apply my understanding of database design principles—from creating tables based on the Third Normal Form (3NF) to ensuring data integrity through the use of primary and foreign keys.

### Database Creation and Table Design

Creating the database and tables from the normalized structure reinforced my understanding of how to implement efficient database schemas. The task required translating the theoretical database design into practical SQL commands to create tables with relationships that maintain referential integrity. I implemented the Students, Courses, Teachers, Exam Boards, and StudentCourses tables, which enabled me to understand how relationships like many-to-many (e.g., students and courses) are handled using a linking table (StudentCourses).

This process also helped me appreciate the significance of primary keys and foreign keys in ensuring data consistency. I learned how primary keys ensure each record is unique, while foreign keys help maintain relationships between tables, preventing invalid data from being inserted.

### Data Insertion

The next step was inserting data into the newly created tables. This part of the task highlighted the importance of data integrity and how normalized tables help reduce redundancy. For instance, separating student information from course details ensured that data like student names and teacher names were not repeated, making the database more efficient.

Inserting data into the StudentCourses table, which links students to courses, teachers, and exam boards, provided practical insight into managing complex relationships between multiple entities. I realized how crucial it is to ensure that all foreign key references exist in the parent tables before inserting data into the child table, which prevents data inconsistencies.

### Testing Referential Integrity

Testing the database for referential integrity was an essential part of the process. I conducted queries to prevent the insertion of records with non-existent foreign keys, ensuring that each foreign key constraint was properly enforced. For instance, attempting to insert a record into StudentCourses with a non-existent student ID failed as expected, demonstrating that the foreign key relationships were correctly established.

I also tested cascade and restrict deletions by attempting to delete a student record that had references in the StudentCourses table. This showed me how relational databases handle cascading deletes or restrict deletions to maintain data integrity across related tables.

### Learning Outcomes

This task greatly enhanced my practical skills in database implementation and SQL scripting. I gained a deeper understanding of how to implement a normalized database structure into a functioning system, focusing on efficiency, data consistency, and referential integrity. I also learned how to handle complex many-to-many relationships in databases, which is critical for real-world applications that involve interconnected data entities.

The testing phase taught me how crucial it is to ensure foreign key constraints are in place to prevent data anomalies, and how cascading deletions help maintain database consistency. This will be incredibly useful in future projects where maintaining data integrity is essential, particularly in large-scale databases.

### Conclusion

Overall, this task was an excellent opportunity to put theory into practice. By designing and building a normalized database, inserting data, and testing the system for integrity, I gained valuable insights into database management. The skills I developed will be directly applicable to future projects where designing and maintaining efficient, scalable databases is crucial.
