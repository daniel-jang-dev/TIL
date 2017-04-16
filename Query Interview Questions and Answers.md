>1. SQL Query to find second highest salary of Employee

    1) SELECT MAX(Salary) FROM employee 
        WHERE salary NOT IN (SELECT MAX(salary) FROM employee);
        
    2) SELECT MAX(salary) FROM employee 
        WHERE salary < (SELECT MAX(salary) FROM employee);
        
    3) SELECT salary FROM (SELECT salary FROM employee 
                           ORDER BY salary DESC LIMIT 2)
        ORDER BY salary LIMIT 1;

>2. SQL Query to find Max Salary from each department.

    SELECT deptID, MAX(salary) FROM employee
     GROUP BY deptID;

>3. These questions become more interesting if Interviewer will ask you to print department name instead of department id, in that case, you need to join Employee table with Department using foreign key DeptID, make sure you do LEFT or RIGHT OUTER JOIN to include departments without any employee as well.

    SELECT DeptName, MAX(Salary) FROM Employee e RIGHT JOIN Department d 
        ON e.DeptId = d.DeptID 
     GROUP BY DeptName;

>4. Write SQL Query to display the current date.

    SELECT GETDATE(); // SQL Server;
    SELECT NOW(); // MySQL

>5. Write an SQL Query to print the name of the distinct employee whose DOB is between 01/01/1960 to 31/12/1975.

    SELECT DISTINCT(name) FROM employee 
     WHERE dob BETWEEN '01/01/1960' AND '31/12/1975';

>6. Write an SQL Query find number of employees according to gender  whose DOB is between 01/01/1960 to 31/12/1975.

    SELECT gender, COUNT(*) FROM employee
     WHERE dob BETWEEN '01/01/1960' AND '31/12/1975'
     GROUP BY gender;

>7. Write an SQL Query to find an employee whose Salary is equal or greater than 10000

    SELECT name FROM employee
     WHERE salary >= 10000;
     
 >8. Write an SQL Query to find name of employee whose name Start with ‘M’

    SELECT name FROM employee
     WHERE name LIKE 'M%';

>9. find all Employee records containing the word "Joe", regardless of whether it was stored as JOE, Joe, or joe.

    SELECT * FROM employee
     WHEWE UPPER(name) LIKE '%JOE%';
 
 >10. Write an SQL Query to find  the year from date.

    SELECT YEAR(GETDATE()); // SQL server
    SELECT YEAR(NOW()); // MySQL
    
>11. Write SQL Query to find duplicate rows in a database? and then write SQL query to delete them?

    SELECT * FROM employee a 
     WHERE rowid = (SELECT MAX(rowid) FROM employee b WHERE a.empno=b.empno);
    
    DELETE FROM employee a 
     WHERE rowid != (SELECT MAX(rowid) FROM employee b WHERE a.empno=b.empno);
     
 >12. There is a table which contains two column Student and Marks, you need to find all the students, whose marks are greater than average marks i.e. list of above average students.

    SELECT student, marks FROM table
     WHERE marks > (SELECT AVG(marks) FROM table);
     
 >13. How do you find all employees which are also manager? You have given a standard employee table with an additional column mgr_id, which contains employee id of the manager.
    
    // employee name, manager name
    SELECT e.name, m.name FROM employee e, employee m 
     WHERE e.mgr_id = m.emp_id;
    
    
