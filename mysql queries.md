# 

##### **write each and every queries including this following topics**



**-- Employee Management System**

**-- SQL Practice Questions and Solutions**

**-- Topics: CRUD, Constraints, Operators, Clauses,**

**-- Aggregate Functions, LIMIT, OFFSET, Aliases, ALTER TABLE**





1\. Display all employees from the employees table.

\--> SELECT \* FROM employees;



2\. Display only first\_name, last\_name, department, and salary of all employees.

\-->SELECT first\_name, last\_name, department, salary FROM employees;



3\. Add a new employee named Tanvi Desai, working as a Developer in IT, with salary 58000, age 25, from Mumbai.

\-->INSERT INTO employees(first\_name,last\_name,department,job\_role,salary,age,city)VALUES('Tanvi','Desai','Developer','IT',58000,25,'mumbai');



4\. Update Tanvi's salary from 58000 to 62000.

\-->UPDATE employees SET salary = 62000 WHERE employee\_id = 16;



5\. Change the city of employee Aarav Sharma from Pune to Mumbai.

\-->UPDATE employees SET city = 'mumbai' WHERE employee\_id = 1;



6\. Delete the employee whose employee\_id is 11.

\-->DELETE FROM employees WHERE employee\_id = 11;



7\. Increase the salary of all IT employees by 10%.

\-->UPDATE employees SET salary = salary \* 1.1 WHERE department = 'IT';



8\. Change the job role of employees working in Sales from Sales Executive to Sales Associate.

\-->UPDATE employees SET job\_role = 'sale\_Associate' WHERE job\_role = 'sales Executive';



9\. Set is\_active = FALSE for employees whose salary is below 40000.

\-->UPDATE employees SET is\_active =FALSE WHERE salary < 40000;



10\. Delete all inactive employees.

\-->DELETE FROM employees WHERE is\_active = FALSE;



\----------------------------------------------------------------------------------------------------------------------------------------------



11\. Find employees whose salary is greater than 60000.

\-->SELECT \* FROM employees WHERE salary > 60000;



12\. Find employees whose salary is between 40000 and 70000.

\-->SELECT \* FROM employees WHERE salary BETWEEN 40000 AND 70000;



13\. Find employees working in either IT, HR, or Finance using the IN operator.

\-->SELECT \* FROM employees WHERE job\_role IN('IT','HR','Finance');



14\. Find employees who are not from Pune.

\-->SELECT \* FROM employees WHERE NOT city ='pune';



15\. Find employees whose age is greater than or equal to 30.

\-->SELECT \* FROM employees WHERE age >= 30;



16\. Find employees whose first name starts with the letter 'A'.

\-->SELECT \* FROM employees WHERE first\_name LIKE 'A%';



17\. Find employees whose email ends with gmail.com.

\-->SELECT \* FROM employees WHERE email LIKE '%gmail.com';



18\. Find employees from Pune whose salary is greater than 50000.

\-->SELECT \* FROM employees WHERE city ='pune' AND salary > 50000;



19\. Display employees from the IT department, ordered by salary from highest to lowest.

\-->SELECT \* FROM employees WHERE department='IT' ORDER BY salary DESC;



20\. Display all employees younger than 30, ordered by age from lowest to highest.

\-->SELECT \* FROM employees WHERE age < 30 ORDER BY age ASC;



\----------------------------------------------------------------------------------------------------------------------------------------------



21\. Display the different cities in which employees live using DISTINCT.

\-->SELECT DISTINCT city FROM employees;



22\. Display the different departments available in the company.

\-->SELECT DISTINCT department FROM employees;



23\. Find employees who joined after 2021-01-01.

\-->SELECT \* FROM employees WHERE joining\_date > '2021-01-01';



24\. Find employees whose experience is between 3 and 8 years.

\-->SELECT \* FROM employees WHERE experience BETWEEN 3 AND 8;



25\. Find active employees from Mumbai whose salary is greater than 50000.

\-->SELECT \* FROM employees WHERE city='Mumbai' AND salary > 50000 AND is\_active = TRUE;



26\. Find the total number of employees in the company.

\-->SELECT COUNT(\*) FROM employees;



27\. Find the average salary of all employees.

\-->SELECT AVG(salary) FROM employees;



28\. Find the highest salary in the company.

\-->SELECT MAX(salary) FROM employees;



29\. Find the lowest salary in the company.

\-->SELECT MIN(salary) FROM employees;



30\. Find the total salary expense of all employees.

\-->SELECT SUM(salary) FROM employees;



\----------------------------------------------------------------------------------------------------------------------------------------------





31\. Display the top 5 highest-paid employees.

\-->SELECT \* FROM employees ORDER BY salary DESC LIMIT 5;



32\. Display the 3 lowest-paid employees.

\-->SELECT \* FROM employees ORDER BY salary ASC LIMIT 3;



33\.  Display first\_name, last\_name, and salary, but show the salary column as Monthly Salary.

\-->SELECT first\_name, last\_name,salary AS monthly\_salary FROM employees;



34\. Display the average salary with the column name Average Salary.

\-->SELECT AVG(salary) AS Average\_Salary FROM employees;



35\. Add a new column called phone\_number with an appropriate datatype.

\-->ALTER TABLE employees ADD phone\_number VARCHAR(10); 



36\. Modify the phone\_number column so that it can store exactly enough characters for an Indian mobile number.

\-->ALTER TABLE employees MODIFY COLUMN phone\_number VARCHAR(50); 



37\. Add a new column called bonus with a suitable numeric datatype and a default value of 0.

\-->ALTER TABLE employees ADD bonus Decimal(10,2) DEFAULT 0;



38\. Add a constraint so that the bonus cannot be negative.

\-->ALTER TABLE employees ADD CONSTRAINT chk\_bonus CHECK(bonus >= 0);











