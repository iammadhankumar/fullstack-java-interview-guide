SELECT DISTINCT salary 
FROM employee A
WHERE (SELECT COUNT(DISTINCT B.salary) FROM employee B WHERE B.salary > A.salary) = 5;

SELECT DISTINCT salary 
FROM employee 
ORDER BY salary DESC 
LIMIT 1 OFFSET 2;

SELECT d.name, SUM(e.salary) AS dept_salary FROM DEPT d JOIN EMPLOYEE_1 e ON e.DEPT_ID=d.DEPT_ID GROUP BY(d.name)
