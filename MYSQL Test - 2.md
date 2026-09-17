#### &#x20;                                           MYSQL Test - 2

#### 

CREATE DATABASE capgemini;

mysql> CREATE DATABASE capgemini;

Query OK, 1 row affected (0.21 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



USE capgemini;

mysql> USE capgemini;

Database changed

\------------------------------------------------------------------------------------------------------------------------------------------------



CREATE TABLE employee (id INT PRIMARY KEY,name VARCHAR(50),profile VARCHAR(50),email VARCHAR(100),salary INT,age INT,experience INT);

mysql> CREATE TABLE employee (id INT PRIMARY KEY,name VARCHAR(50),profile VARCHAR(50),email VARCHAR(100),salary INT,age INT,experience INT);

Query OK, 0 rows affected (0.23 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



DESC employee;

mysql> DESC employee;

+------------+--------------+------+-----+---------+-------+

| Field      | Type         | Null | Key | Default | Extra |

+------------+--------------+------+-----+---------+-------+

| id         | int          | NO   | PRI | NULL    |       |

| name       | varchar(50)  | YES  |     | NULL    |       |

| profile    | varchar(50)  | YES  |     | NULL    |       |

| email      | varchar(100) | YES  |     | NULL    |       |

| salary     | int          | YES  |     | NULL    |       |

| age        | int          | YES  |     | NULL    |       |

| experience | int          | YES  |     | NULL    |       |

+------------+--------------+------+-----+---------+-------+

7 rows in set (0.06 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



INSERT INTO employee (id, name, profile, email, salary, age, experience)VALUES

(1, 'rani', 'dev',  'rani@gmail.com', 11000, 43, 27),

(2, 'raj',  'test', 'raj@gmail.com',  21000, 33, 17),

(3, 'radha','test', 'radha@gmail.com',26000, 38, 21),

(4, 'raj',  'dev',  'raj12@gmail.com',51000, 32, 12),

(5, 'john', 'dev',  'john@gmail.com', 51000, 39, 27);

\------------------------------------------------------------------------------------------------------------------------------------------------



SELECT \* FROM employee;

mysql> SELECT \* FROM employee;

+----+-------+---------+-----------------+--------+------+------------+

| id | name  | profile | email           | salary | age  | experience |

+----+-------+---------+-----------------+--------+------+------------+

|  1 | rani  | dev     | rani@gmail.com  |  11000 |   43 |         27 |

|  2 | raj   | test    | raj@gmail.com   |  21000 |   33 |         17 |

|  3 | radha | test    | radha@gmail.com |  26000 |   38 |         21 |

|  4 | raj   | dev     | raj12@gmail.com |  51000 |   32 |         12 |

|  5 | john  | dev     | john@gmail.com  |  51000 |   39 |         27 |

+----+-------+---------+-----------------+--------+------+------------+

5 rows in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



1\. As a user, I want to add an column branch\_location so I can

efficiently search the branch wise record.

\-->ALTER TABLE employee ADD branch\_location VARCHAR(50);

mysql> ALTER TABLE employee ADD branch\_location VARCHAR(50);

Query OK, 0 rows affected (0.09 sec)

Records: 0  Duplicates: 0  Warnings: 0



mysql> DESC employee;

+-----------------+--------------+------+-----+---------+-------+

| Field           | Type         | Null | Key | Default | Extra |

+-----------------+--------------+------+-----+---------+-------+

| id              | int          | NO   | PRI | NULL    |       |

| name            | varchar(50)  | YES  |     | NULL    |       |

| profile         | varchar(50)  | YES  |     | NULL    |       |

| email           | varchar(100) | YES  |     | NULL    |       |

| salary          | int          | YES  |     | NULL    |       |

| age             | int          | YES  |     | NULL    |       |

| experience      | int          | YES  |     | NULL    |       |

| branch\_location | varchar(50)  | YES  |     | NULL    |       |

+-----------------+--------------+------+-----+---------+-------+

8 rows in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



2\. As a user, I want to check the total salary expenses on employees.

\-->SELECT SUM(salary) AS total\_salary FROM employee;

mysql> SELECT SUM(salary) AS total\_salary FROM employee;

+--------------+

| total\_salary |

+--------------+

|       160000 |

+--------------+

1 row in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



3\. As a user, I want to see the max salary of employee from test

profile.

\-->SELECT MAX(salary) FROM employee WHERE profile='test';

mysql> SELECT MAX(salary) FROM employee WHERE profile='test';

+-------------+

| MAX(salary) |

+-------------+

|       26000 |

+-------------+

1 row in set (0.01 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



4\. As a user I want to get the average experience level of employees.

\--> SELECT AVG(experience) AS average\_experience FROM employee;

mysql> SELECT AVG(experience) AS average\_experience FROM employee;

+--------------------+

| average\_experience |

+--------------------+

|            20.8000 |

+--------------------+

1 row in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



5\. As a user I want to see the name of highest paid employee.

\-->SELECT name FROM employee WHERE salary=(SELECT MAX(salary) AS highest\_salary FROM employee);

mysql> SELECT name FROM employee WHERE salary =(SELECT MAX(salary) AS highest\_salary FROM employee);

+------+

| name |

+------+

| raj  |

| john |

+------+

2 rows in set (0.00 sec) 

\------------------------------------------------------------------------------------------------------------------------------------------------



6\. As a user, I want to see the name and experience of lowest paid employee.

\-->SELECT name, experience FROM employee WHERE salary =(SELECT MIN(salary) FROM employee);

mysql> SELECT name, experience FROM employee WHERE salary =(SELECT MIN(salary) FROM employee);

+------+------------+

| name | experience |

+------+------------+

| rani |         27 |

+------+------------+

1 row in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



7\. As a user I want check how many employees are working in

company.

\-->SELECT COUNT(\*) AS employees FROM employee; 

mysql> SELECT COUNT(\*) AS employees FROM employee;

+-----------+

| employees |

+-----------+

|         5 |

+-----------+

1 row in set (0.01 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



8\. As a user I want to see those employee names who are from test profile and having salary more than 25K.

\--> SELECT name FROM employee WHERE profile = 'test' AND salary > 25000;

mysql> SELECT name FROM employee WHERE profile = 'test' AND salary > 25000;

+-------+

| name  |

+-------+

| radha |

+-------+

1 row in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



9\. As a user, I want to shift Radha on support profile.

\--> UPDATE employee SET profile = 'support' WHERE name = 'radha';

mysql> UPDATE employee SET profile = 'support' WHERE name = 'radha';

Query OK, 1 row affected (0.01 sec)

Rows matched: 1  Changed: 1  Warnings: 0



mysql> SELECT \* FROM employee;

+----+-------+---------+-----------------+--------+------+------------+-----------------+

| id | name  | profile | email           | salary | age  | experience | branch\_location |

+----+-------+---------+-----------------+--------+------+------------+-----------------+

|  1 | rani  | dev     | rani@gmail.com  |  11000 |   43 |         27 | NULL            |

|  2 | raj   | test    | raj@gmail.com   |  21000 |   33 |         17 | NULL            |

|  3 | radha | support | radha@gmail.com |  26000 |   38 |         21 | NULL            |

|  4 | raj   | dev     | raj12@gmail.com |  51000 |   32 |         12 | NULL            |

|  5 | john  | dev     | john@gmail.com  |  51000 |   39 |         27 | NULL            |

+----+-------+---------+-----------------+--------+------+------------+-----------------+

5 rows in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



10\. As a user, I want to get the second highest salary of employee.

\-->SELECT MAX(salary) AS second\_highest FROM employee WHERE salary <(SELECT MAX(salary) FROM employee);

mysql> SELECT MAX(salary) AS second\_highest FROM employee WHERE salary <(SELECT MAX(salary) FROM employee);

+----------------+

| second\_highest |

+----------------+

|          26000 |

+----------------+

1 row in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



11\. As a user I want to get the second lowest salary of employee.

\--> SELECT MIN(salary) AS second\_lowest FROM employee WHERE salary >(SELECT MIN(salary) FROM employee);

mysql> SELECT MIN(salary) AS second\_lowest FROM employee WHERE salary >(SELECT MIN(salary) FROM employee);

+---------------+

| second\_lowest |

+---------------+

|         21000 |

+---------------+

1 row in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



12\. As a user, I want to calculate the average salary of employees

those are belongs to dev profile.

\--> SELECT AVG(salary) AS average\_salary FROM employee WHERE profile = 'dev'; 

mysql> SELECT AVG(salary) AS average\_salary FROM employee WHERE profile = 'dev';

+----------------+

| average\_salary |

+----------------+

|     37666.6667 |

+----------------+

1 row in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



13\. As a user, I want to see the employee’s name and salary who is

having lowest experience.

\--> SELECT name,salary FROM employee WHERE experience =(SELECT MIN(experience) FROM employee); 

mysql> SELECT name,salary FROM employee WHERE experience =(SELECT MIN(experience) FROM employee);

+------+--------+

| name | salary |

+------+--------+

| raj  |  51000 |

+------+--------+

1 row in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



14\. As a user, I want to see the employee name who is having lowest

age with max salary.

\--> SELECT name FROM employee WHERE salary =(SELECT MAX(salary) FROM employee) ORDER BY age LIMIT 1;

mysql> SELECT name FROM employee WHERE salary =(SELECT MAX(salary) FROM employee) ORDER BY age LIMIT 1;

+------+

| name |

+------+

| raj  |

+------+

1 row in set (0.00 sec)



\-->SELECT name FROM employee WHERE salary =(SELECT MAX(salary) FROM employee)AND age =(SELECT MIN(age) FROM employee);

mysql> SELECT name FROM employee WHERE salary =(SELECT MAX(salary) FROM employee)AND age =(SELECT MIN(age) FROM employee);

+------+

| name |

+------+

| raj  |

+------+

1 row in set (0.00 sec)

\------------------------------------------------------------------------------------------------------------------------------------------------



15\. As a user, I want to remove all the employee from company.

\-->DELETE FROM employee;

