---
layout: post
title: UoE - Deciphering Big Data July 2024 - Normalisation Task
subtitle: Critically analyse data wrangling problems and determine appropriate methodologies, tools, and techniques (involving preparing, cleaning, exploring, creating, optimising and evaluating big data) to solve them. Design, develop and evaluate solutions for processing datasets and solving complex problems in various environments using relevant programming paradigms. Systematically develop and implement the skills required to be effective member of a development team in a virtual professional environment, adopting real life perspectives on team roles and organisation.
categories: EL-Activities
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Normalisation Task
---

### Step 1: Convert Data into 1NF (First Normal Form)

1NF Requirements:
- Eliminate repeating groups by ensuring that each cell contains a single value.
- Each record (row) should be unique.

The original table contains repeating groups such as multiple courses, exam boards, and teachers for each student. To convert this data into 1NF, we need to ensure each row contains atomic values.

#### 1NF Table:

![image](/assets/images/banners/normal_task_unit7.png)

### Step 2: Convert Data into 2NF (Second Normal Form)

2NF Requirements:
- The table must meet all 1NF requirements.
- Eliminate partial dependency, meaning that all non-primary attributes should be fully dependent on the primary key.

In 1NF, the composite primary key is Student Number + Course Name because a student can take multiple courses. However, the attributes Student Name, Exam Score, Support, and Date of Birth are only dependent on the Student Number, not the Course Name. Therefore, we need to split the table into two tables: one for student information and another for course information.

#### 2NF Tables:

Students Table:

![image](/assets/images/banners/normal_unit7_1.png)

Courses Table:

![image](/assets/images/banners/normal_unit7_2.png)

### Step 3: Convert Data into 3NF (Third Normal Form)

3NF Requirements:
- The table must meet all 2NF requirements.
- There should be no transitive dependency, i.e., non-primary attributes should not depend on other non-primary attributes.

In the Courses Table, Teacher Name is dependent on both Course Name and Exam Board, not just on the Student Number. Therefore, we can split the Courses Table into two tables: one for course assignments and one for course-teacher relationships.

#### 3NF Tables:

Students Table:

![image](/assets/images/banners/normal_unit7_3.png)

Student Courses Table:

![image](/assets/images/banners/normal_unit7_4.png)

Course Details Table:

![image](/assets/images/banners/normal_unit7_5.png)

### Final Normalised Data (3NF)

Now, the data is in 3NF with all tables containing atomic data and no redundant or unnecessary dependencies. Each table is focused on a single entity, allowing for efficient data management and queries.

---
## Individual Reflecion
---

### Reflection

The Normalisation Task provided an excellent opportunity to solidify my understanding of the normalisation process and its importance in database design. The task required converting data from an unstructured format into 1NF, 2NF, and finally 3NF, ensuring that the resulting tables were free of redundancy and well-organized for efficient data storage and retrieval.

### Step 1: First Normal Form (1NF)

In the first step, I had to eliminate repeating groups and ensure that each row in the table contained atomic values. This part of the task highlighted the importance of data integrity at the most basic level. By converting the original data into 1NF, I ensured that each record contained only one piece of information per cell. This process helped me appreciate how unstructured data can introduce inefficiencies and inconsistencies, which 1NF helps to address.

### Step 2: Second Normal Form (2NF)

The transition to 2NF required identifying and eliminating partial dependencies. I learned to recognize when non-primary attributes were dependent only on part of a composite primary key, rather than the entire key. By splitting the table into two (one focused on student information and the other on course information), I removed partial dependencies and reduced redundancy. This step helped me understand how poorly designed databases can result in data anomalies, and how 2NF helps prevent them by organizing data into more meaningful entities.

### Step 3: Third Normal Form (3NF)

In the final step, I had to ensure the data met the requirements of 3NF, which involved eliminating transitive dependencies. By splitting the Courses Table into one for course assignments and another for course-teacher relationships, I ensured that non-primary attributes only depended on the primary key. This step clarified for me the importance of focusing on each entity’s attributes and ensuring that no unnecessary relationships exist, leading to a cleaner and more efficient database structure.

### Overall Learning and Application

This task reinforced the value of normalisation in database design. By moving the data through the stages of normalisation, I learned how to structure databases in a way that improves data integrity, reduces redundancy, and enhances query performance. These concepts are particularly relevant in my current work with databases, as ensuring efficient storage and easy retrieval of data is essential for scalability.

Additionally, the exercise gave me practical experience in decomposing complex datasets and restructuring them to optimize their design. This hands-on application will be useful in future projects, particularly when dealing with large-scale databases where redundancy and inefficiencies can lead to performance issues.



