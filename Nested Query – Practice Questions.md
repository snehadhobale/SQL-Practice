#### &#x20;                            Nested Query – Practice Questions

#### 

1. Find students who scored more than Rahul.

\--> SELECT \* FROM students WHERE marks < (SELECT marks FROM students where name = 'Rahul');


2\. Find students who scored less than Priya.
-->  SELECT \* FROM students WHERE marks < (SELECT marks FROM students where name = 'Priya');


3\. Find students having the same marks as Rohit.
--> SELECT \* FROM students WHERE marks = (SELECT marks FROM students where name = 'Rohit');


4\. Find students older than Amit.          
--> SELECT \* FROM students WHERE age < (SELECT age FROM students WHERE name = 'Amit');           


5\. Find students younger than Sneha.

\--> SELECT \* FROM students WHERE age > (SELECT age FROM students WHERE name = 'Sneha');



6\. Find students who scored above the average marks.
--> SELECT AVG(marks) FROM students WHERE marks <(SELECT AVG(marks) FROM students);


7\. Find students who scored below the average marks.
-->SELECT AVG(marks) FROM students WHERE marks >(SELECT AVG(marks) FROM students);


8\. Find the student with the highest marks.
--> SELECT MAX(marks) FROM students


9\. Find the student with the lowest marks.
--> SELECT MIN(marks) FROM students;


10\. Find students whose marks are equal to the maximum marks.
--> SELECT \* FROM students WHERE marks =(SELECT MAX(marks) FROM students);


11\. Find students whose marks are greater than the maximum marks of students from Mumbai.
-->SELECT \* FROM students WHERE marks =(SELECT MAX(marks) FROM students WHERE city = 'mumbai');


12\. Find students whose marks are less than the minimum marks of students from Pune.
-->SELECT \* FROM students WHERE marks < (SELECT MIN(marks) FROM students WHERE city = 'pune');


13\. Find students who are enrolled in the same course as Rahul.
-->SELECT \* FROM students WHERE course IN(SELECT course FROM students WHERE name = 'Rahul');


14\. Find students whose age is present among Mumbai students.
--> SELECT \* FROM students WHERE age IN(SELECT age FROM students WHERE city = 'mumbai');



15\. Find students whose marks are present among Pune students.

\--> SELECT \* FROM students WHERE marks IN(SELECT marks FROM students WHERE city = 'pune');





mysql> CREATE TABLE students (

&#x20;   ->     student\_id INT PRIMARY KEY AUTO\_INCREMENT,

&#x20;   ->     name VARCHAR(50),

&#x20;   ->     marks INT,

&#x20;   ->     age INT,

&#x20;   ->     city VARCHAR(50),

&#x20;   ->     course VARCHAR(50)

&#x20;   -> );

Query OK, 0 rows affected (0.69 sec)



mysql> DESC students;

+------------+-------------+------+-----+---------+----------------+

| Field      | Type        | Null | Key | Default | Extra          |

+------------+-------------+------+-----+---------+----------------+

| student\_id | int         | NO   | PRI | NULL    | auto\_increment |

| name       | varchar(50) | YES  |     | NULL    |                |

| marks      | int         | YES  |     | NULL    |                |

| age        | int         | YES  |     | NULL    |                |

| city       | varchar(50) | YES  |     | NULL    |                |

| course     | varchar(50) | YES  |     | NULL    |                |

+------------+-------------+------+-----+---------+----------------+

6 rows in set (0.21 sec)



mysql> INSERT INTO students (name, marks, age, city, course)

&#x20;   -> VALUES

&#x20;   -> ('Rahul', 85, 21, 'Mumbai', 'Java'),

&#x20;   -> ('Priya', 72, 22, 'Pune', 'Python'),

&#x20;   -> ('Rohit', 90, 20, 'Mumbai', 'Java'),

&#x20;   -> ('Sneha', 78, 21, 'Pune', 'Python'),

&#x20;   -> ('Amit', 65, 23, 'Delhi', 'Java'),

&#x20;   -> ('Neha', 88, 20, 'Mumbai', 'Data Science'),

&#x20;   -> ('Vikas', 55, 24, 'Pune', 'Java'),

&#x20;   -> ('Pooja', 92, 21, 'Mumbai', 'Python'),

&#x20;   -> ('Karan', 70, 22, 'Delhi', 'Data Science'),

&#x20;   -> ('Anjali', 81, 20, 'Pune', 'Java'),

&#x20;   -> ('Suresh', 60, 23, 'Mumbai', 'Python'),

&#x20;   -> ('Riya', 95, 21, 'Pune', 'Data Science'),

&#x20;   -> ('Akash', 75, 22, 'Mumbai', 'Java'),

&#x20;   -> ('Nikita', 68, 20, 'Delhi', 'Python'),

&#x20;   -> ('Manish', 84, 24, 'Pune', 'Java'),

&#x20;   -> ('Shreya', 91, 21, 'Mumbai', 'Data Science'),

&#x20;   -> ('Aditya', 58, 23, 'Pune', 'Python'),

&#x20;   -> ('Kavya', 79, 20, 'Mumbai', 'Java'),

&#x20;   -> ('Nikhil', 87, 22, 'Pune', 'Data Science'),

&#x20;   -> ('Isha', 73, 21, 'Mumbai', 'Python'),

&#x20;   -> ('Varun', 96, 23, 'Delhi', 'Java'),

&#x20;   -> ('Meena', 64, 22, 'Pune', 'Python'),

&#x20;   -> ('Arjun', 89, 20, 'Mumbai', 'Data Science'),

&#x20;   -> ('Divya', 76, 21, 'Pune', 'Java'),

&#x20;   -> ('Sameer', 50, 24, 'Mumbai', 'Python');

Query OK, 25 rows affected (0.05 sec)

Records: 25  Duplicates: 0  Warnings: 0



mysql> SELECT \* FROM students;

+------------+--------+-------+------+--------+--------------+

| student\_id | name   | marks | age  | city   | course       |

+------------+--------+-------+------+--------+--------------+

|          1 | Rahul  |    85 |   21 | Mumbai | Java         |

|          2 | Priya  |    72 |   22 | Pune   | Python       |

|          3 | Rohit  |    90 |   20 | Mumbai | Java         |

|          4 | Sneha  |    78 |   21 | Pune   | Python       |

|          5 | Amit   |    65 |   23 | Delhi  | Java         |

|          6 | Neha   |    88 |   20 | Mumbai | Data Science |

|          7 | Vikas  |    55 |   24 | Pune   | Java         |

|          8 | Pooja  |    92 |   21 | Mumbai | Python       |

|          9 | Karan  |    70 |   22 | Delhi  | Data Science |

|         10 | Anjali |    81 |   20 | Pune   | Java         |

|         11 | Suresh |    60 |   23 | Mumbai | Python       |

|         12 | Riya   |    95 |   21 | Pune   | Data Science |

|         13 | Akash  |    75 |   22 | Mumbai | Java         |

|         14 | Nikita |    68 |   20 | Delhi  | Python       |

|         15 | Manish |    84 |   24 | Pune   | Java         |

|         16 | Shreya |    91 |   21 | Mumbai | Data Science |

|         17 | Aditya |    58 |   23 | Pune   | Python       |

|         18 | Kavya  |    79 |   20 | Mumbai | Java         |

|         19 | Nikhil |    87 |   22 | Pune   | Data Science |

|         20 | Isha   |    73 |   21 | Mumbai | Python       |

|         21 | Varun  |    96 |   23 | Delhi  | Java         |

|         22 | Meena  |    64 |   22 | Pune   | Python       |

|         23 | Arjun  |    89 |   20 | Mumbai | Data Science |

|         24 | Divya  |    76 |   21 | Pune   | Java         |

|         25 | Sameer |    50 |   24 | Mumbai | Python       |

+------------+--------+-------+------+--------+--------------+

25 rows in set (0.00 sec)



mysql> SELECT \* FROM students WHERE marks < (SELECT marks FROM students where name = 'Rahul');

+------------+--------+-------+------+--------+--------------+

| student\_id | name   | marks | age  | city   | course       |

+------------+--------+-------+------+--------+--------------+

|          2 | Priya  |    72 |   22 | Pune   | Python       |

|          4 | Sneha  |    78 |   21 | Pune   | Python       |

|          5 | Amit   |    65 |   23 | Delhi  | Java         |

|          7 | Vikas  |    55 |   24 | Pune   | Java         |

|          9 | Karan  |    70 |   22 | Delhi  | Data Science |

|         10 | Anjali |    81 |   20 | Pune   | Java         |

|         11 | Suresh |    60 |   23 | Mumbai | Python       |

|         13 | Akash  |    75 |   22 | Mumbai | Java         |

|         14 | Nikita |    68 |   20 | Delhi  | Python       |

|         15 | Manish |    84 |   24 | Pune   | Java         |

|         17 | Aditya |    58 |   23 | Pune   | Python       |

|         18 | Kavya  |    79 |   20 | Mumbai | Java         |

|         20 | Isha   |    73 |   21 | Mumbai | Python       |

|         22 | Meena  |    64 |   22 | Pune   | Python       |

|         24 | Divya  |    76 |   21 | Pune   | Java         |

|         25 | Sameer |    50 |   24 | Mumbai | Python       |

+------------+--------+-------+------+--------+--------------+

16 rows in set (0.05 sec)



mysql> SELECT \* FROM students WHERE marks < (SELECT marks FROM students where name = 'Priya');

+------------+--------+-------+------+--------+--------------+

| student\_id | name   | marks | age  | city   | course       |

+------------+--------+-------+------+--------+--------------+

|          5 | Amit   |    65 |   23 | Delhi  | Java         |

|          7 | Vikas  |    55 |   24 | Pune   | Java         |

|          9 | Karan  |    70 |   22 | Delhi  | Data Science |

|         11 | Suresh |    60 |   23 | Mumbai | Python       |

|         14 | Nikita |    68 |   20 | Delhi  | Python       |

|         17 | Aditya |    58 |   23 | Pune   | Python       |

|         22 | Meena  |    64 |   22 | Pune   | Python       |

|         25 | Sameer |    50 |   24 | Mumbai | Python       |

+------------+--------+-------+------+--------+--------------+

8 rows in set (0.00 sec)



mysql> SELECT \* FROM students WHERE marks = (SELECT marks FROM students where name = 'Rohit');

+------------+-------+-------+------+--------+--------+

| student\_id | name  | marks | age  | city   | course |

+------------+-------+-------+------+--------+--------+

|          3 | Rohit |    90 |   20 | Mumbai | Java   |

+------------+-------+-------+------+--------+--------+

1 row in set (0.00 sec)



mysql> SELECT \* FROM students WHERE age < (SELECT age FROM students WHERE name = 'Amit');

+------------+--------+-------+------+--------+--------------+

| student\_id | name   | marks | age  | city   | course       |

+------------+--------+-------+------+--------+--------------+

|          1 | Rahul  |    85 |   21 | Mumbai | Java         |

|          2 | Priya  |    72 |   22 | Pune   | Python       |

|          3 | Rohit  |    90 |   20 | Mumbai | Java         |

|          4 | Sneha  |    78 |   21 | Pune   | Python       |

|          6 | Neha   |    88 |   20 | Mumbai | Data Science |

|          8 | Pooja  |    92 |   21 | Mumbai | Python       |

|          9 | Karan  |    70 |   22 | Delhi  | Data Science |

|         10 | Anjali |    81 |   20 | Pune   | Java         |

|         12 | Riya   |    95 |   21 | Pune   | Data Science |

|         13 | Akash  |    75 |   22 | Mumbai | Java         |

|         14 | Nikita |    68 |   20 | Delhi  | Python       |

|         16 | Shreya |    91 |   21 | Mumbai | Data Science |

|         18 | Kavya  |    79 |   20 | Mumbai | Java         |

|         19 | Nikhil |    87 |   22 | Pune   | Data Science |

|         20 | Isha   |    73 |   21 | Mumbai | Python       |

|         22 | Meena  |    64 |   22 | Pune   | Python       |

|         23 | Arjun  |    89 |   20 | Mumbai | Data Science |

|         24 | Divya  |    76 |   21 | Pune   | Java         |

+------------+--------+-------+------+--------+--------------+

18 rows in set (0.00 sec)



mysql> SELECT \* FROM students WHERE age > (SELECT age FROM students WHERE name = 'Sneha');

+------------+--------+-------+------+--------+--------------+

| student\_id | name   | marks | age  | city   | course       |

+------------+--------+-------+------+--------+--------------+

|          2 | Priya  |    72 |   22 | Pune   | Python       |

|          5 | Amit   |    65 |   23 | Delhi  | Java         |

|          7 | Vikas  |    55 |   24 | Pune   | Java         |

|          9 | Karan  |    70 |   22 | Delhi  | Data Science |

|         11 | Suresh |    60 |   23 | Mumbai | Python       |

|         13 | Akash  |    75 |   22 | Mumbai | Java         |

|         15 | Manish |    84 |   24 | Pune   | Java         |

|         17 | Aditya |    58 |   23 | Pune   | Python       |

|         19 | Nikhil |    87 |   22 | Pune   | Data Science |

|         21 | Varun  |    96 |   23 | Delhi  | Java         |

|         22 | Meena  |    64 |   22 | Pune   | Python       |

|         25 | Sameer |    50 |   24 | Mumbai | Python       |

+------------+--------+-------+------+--------+--------------+

12 rows in set (0.00 sec)



mysql> SELECT AVG(marks) FROM students WHERE marks <(SELECT AVG(marks) FROM students);

+------------+

| AVG(marks) |

+------------+

|    65.5000 |

+------------+

1 row in set (0.00 sec)



mysql> SELECT AVG(marks) FROM students WHERE marks >(SELECT AVG(marks) FROM students);

+------------+

| AVG(marks) |

+------------+

|    87.3077 |

+------------+

1 row in set (0.00 sec)



mysql> SELECT MAX(marks) FROM students WHERE marks < (SELECT MIN(marks) FROM students);

+------------+

| MAX(marks) |

+------------+

|       NULL |

+------------+

1 row in set (0.00 sec)



mysql> SELECT MAX(marks) FROM students;

+------------+

| MAX(marks) |

+------------+

|         96 |

+------------+

1 row in set (0.00 sec)



mysql> SELECT MIN(marks) FROM students;

+------------+

| MIN(marks) |

+------------+

|         50 |

+------------+

1 row in set (0.00 sec)



mysql> SELECT \* FROM students WHERE marks =(SELECT MAX(marks) FROM students);

+------------+-------+-------+------+-------+--------+

| student\_id | name  | marks | age  | city  | course |

+------------+-------+-------+------+-------+--------+

|         21 | Varun |    96 |   23 | Delhi | Java   |

+------------+-------+-------+------+-------+--------+

1 row in set (0.00 sec)



mysql> SELECT \* FROM students WHERE marks =(SELECT MAX(marks) FROM students WHERE city = 'mumbai');

+------------+-------+-------+------+--------+--------+

| student\_id | name  | marks | age  | city   | course |

+------------+-------+-------+------+--------+--------+

|          8 | Pooja |    92 |   21 | Mumbai | Python |

+------------+-------+-------+------+--------+--------+

1 row in set (0.00 sec)



mysql> SELECT \* FROM students WHERE marks < (SELECT MIN(marks) FROM students WHERE city = 'pune');

+------------+--------+-------+------+--------+--------+

| student\_id | name   | marks | age  | city   | course |

+------------+--------+-------+------+--------+--------+

|         25 | Sameer |    50 |   24 | Mumbai | Python |

+------------+--------+-------+------+--------+--------+

1 row in set (0.00 sec)



mysql> SELECT \* FROM students WHERE course IN(SELECT course FROM students WHERE name = 'Rahul');

+------------+--------+-------+------+--------+--------+

| student\_id | name   | marks | age  | city   | course |

+------------+--------+-------+------+--------+--------+

|          1 | Rahul  |    85 |   21 | Mumbai | Java   |

|          3 | Rohit  |    90 |   20 | Mumbai | Java   |

|          5 | Amit   |    65 |   23 | Delhi  | Java   |

|          7 | Vikas  |    55 |   24 | Pune   | Java   |

|         10 | Anjali |    81 |   20 | Pune   | Java   |

|         13 | Akash  |    75 |   22 | Mumbai | Java   |

|         15 | Manish |    84 |   24 | Pune   | Java   |

|         18 | Kavya  |    79 |   20 | Mumbai | Java   |

|         21 | Varun  |    96 |   23 | Delhi  | Java   |

|         24 | Divya  |    76 |   21 | Pune   | Java   |

+------------+--------+-------+------+--------+--------+

10 rows in set (0.01 sec)



mysql> SELECT \* FROM students WHERE course = (SELECT course FROM students WHERE name = 'Rahul');

+------------+--------+-------+------+--------+--------+

| student\_id | name   | marks | age  | city   | course |

+------------+--------+-------+------+--------+--------+

|          1 | Rahul  |    85 |   21 | Mumbai | Java   |

|          3 | Rohit  |    90 |   20 | Mumbai | Java   |

|          5 | Amit   |    65 |   23 | Delhi  | Java   |

|          7 | Vikas  |    55 |   24 | Pune   | Java   |

|         10 | Anjali |    81 |   20 | Pune   | Java   |

|         13 | Akash  |    75 |   22 | Mumbai | Java   |

|         15 | Manish |    84 |   24 | Pune   | Java   |

|         18 | Kavya  |    79 |   20 | Mumbai | Java   |

|         21 | Varun  |    96 |   23 | Delhi  | Java   |

|         24 | Divya  |    76 |   21 | Pune   | Java   |

+------------+--------+-------+------+--------+--------+

10 rows in set (0.00 sec)



mysql> SELECT \* FROM students WHERE age IN(SELECT age FROM students WHERE city = 'mumbai');

+------------+--------+-------+------+--------+--------------+

| student\_id | name   | marks | age  | city   | course       |

+------------+--------+-------+------+--------+--------------+

|          1 | Rahul  |    85 |   21 | Mumbai | Java         |

|          2 | Priya  |    72 |   22 | Pune   | Python       |

|          3 | Rohit  |    90 |   20 | Mumbai | Java         |

|          4 | Sneha  |    78 |   21 | Pune   | Python       |

|          5 | Amit   |    65 |   23 | Delhi  | Java         |

|          6 | Neha   |    88 |   20 | Mumbai | Data Science |

|          7 | Vikas  |    55 |   24 | Pune   | Java         |

|          8 | Pooja  |    92 |   21 | Mumbai | Python       |

|          9 | Karan  |    70 |   22 | Delhi  | Data Science |

|         10 | Anjali |    81 |   20 | Pune   | Java         |

|         11 | Suresh |    60 |   23 | Mumbai | Python       |

|         12 | Riya   |    95 |   21 | Pune   | Data Science |

|         13 | Akash  |    75 |   22 | Mumbai | Java         |

|         14 | Nikita |    68 |   20 | Delhi  | Python       |

|         15 | Manish |    84 |   24 | Pune   | Java         |

|         16 | Shreya |    91 |   21 | Mumbai | Data Science |

|         17 | Aditya |    58 |   23 | Pune   | Python       |

|         18 | Kavya  |    79 |   20 | Mumbai | Java         |

|         19 | Nikhil |    87 |   22 | Pune   | Data Science |

|         20 | Isha   |    73 |   21 | Mumbai | Python       |

|         21 | Varun  |    96 |   23 | Delhi  | Java         |

|         22 | Meena  |    64 |   22 | Pune   | Python       |

|         23 | Arjun  |    89 |   20 | Mumbai | Data Science |

|         24 | Divya  |    76 |   21 | Pune   | Java         |

|         25 | Sameer |    50 |   24 | Mumbai | Python       |

+------------+--------+-------+------+--------+--------------+

25 rows in set (0.00 sec)



mysql> SELECT \* FROM students WHERE marks IN(SELECT marks FROM students WHERE city = 'pune');

+------------+--------+-------+------+------+--------------+

| student\_id | name   | marks | age  | city | course       |

+------------+--------+-------+------+------+--------------+

|          2 | Priya  |    72 |   22 | Pune | Python       |

|          4 | Sneha  |    78 |   21 | Pune | Python       |

|          7 | Vikas  |    55 |   24 | Pune | Java         |

|         10 | Anjali |    81 |   20 | Pune | Java         |

|         12 | Riya   |    95 |   21 | Pune | Data Science |

|         15 | Manish |    84 |   24 | Pune | Java         |

|         17 | Aditya |    58 |   23 | Pune | Python       |

|         19 | Nikhil |    87 |   22 | Pune | Data Science |

|         22 | Meena  |    64 |   22 | Pune | Python       |

|         24 | Divya  |    76 |   21 | Pune | Java         |

+------------+--------+-------+------+------+--------------+

10 rows in set (0.00 sec)



mysql>

