# SQL Lab – Experiment 7

## Aim

To perform aggregate functions, grouping, date calculations, matrix queries, and analytical queries using SQL.

---

## Question 1

Compute the number of days remaining in the current year.

### Query

```sql
SELECT (TO_DATE('31-DEC-' || TO_CHAR(SYSDATE, 'YYYY'), 'DD-MON-YYYY') - SYSDATE) AS DAYS_LEFT
FROM DUAL;
```

### Output

| DAYS_LEFT |
| --------- |
| 275       |

---

## Question 2

Find the highest and lowest salaries and the difference between them.

### Query

```sql
SELECT MAX(SAL) AS HIGHEST_SALARY,
       MIN(SAL) AS LOWEST_SALARY,
       (MAX(SAL) - MIN(SAL)) AS DIFFERENCE
FROM EMPLOYEE;
```

### Output

| HIGHEST_SALARY | LOWEST_SALARY | DIFFERENCE |
| -------------- | ------------- | ---------- |
| 5000           | 800           | 4200       |

---

## Question 3

List employees whose commission is greater than 25% of their salary.

### Query

```sql
SELECT ENAME, SAL, COMM
FROM EMPLOYEE
WHERE COMM > (0.25 * SAL);
```

### Output

| ENAME  | SAL  | COMM |
| ------ | ---- | ---- |
| ALLEN  | 1600 | 300  |
| MARTIN | 1250 | 500  |

---

## Question 4

Display salary in dollar format.

### Query

```sql
SELECT ENAME, TO_CHAR(SAL, '$9999.99') AS SALARY
FROM EMPLOYEE;
```

### Output

| ENAME  | SALARY   |
| ------ | -------- |
| SMITH  | $800.00  |
| ALLEN  | $1600.00 |
| WARD   | $1250.00 |
| JONES  | $2975.00 |
| MARTIN | $1250.00 |
| BLAKE  | $2850.00 |
| CLARK  | $2450.00 |
| SCOTT  | $3000.00 |
| KING   | $5000.00 |
| TURNER | $1500.00 |
| ADAMS  | $1100.00 |
| JAMES  | $950.00  |
| FORD   | $3000.00 |
| MILLER | $1300.00 |

---

## Question 5

Create a matrix query to display job-wise salary based on department and total salary.

### Query

```sql
SELECT JOB,
       SUM(CASE WHEN DEPTNO = 10 THEN SAL END) AS DEPT10,
       SUM(CASE WHEN DEPTNO = 20 THEN SAL END) AS DEPT20,
       SUM(CASE WHEN DEPTNO = 30 THEN SAL END) AS DEPT30,
       SUM(SAL) AS TOTAL
FROM EMPLOYEE
GROUP BY JOB;
```

### Output

| JOB       | DEPT10 | DEPT20 | DEPT30 | TOTAL |
| --------- | ------ | ------ | ------ | ----- |
| CLERK     | 1300   | 1900   | 950    | 4150  |
| MANAGER   | 2450   | 2975   | 2850   | 8275  |
| SALESMAN  | NULL   | NULL   | 5600   | 5600  |
| ANALYST   | NULL   | 6000   | NULL   | 6000  |
| PRESIDENT | 5000   | NULL   | NULL   | 5000  |

---

## Question 6

Display total number of employees and count of employees hired in specific years.

### Query

```sql
SELECT COUNT(*) AS TOTAL_EMP,
       SUM(CASE WHEN EXTRACT(YEAR FROM HIREDATE) = 1980 THEN 1 ELSE 0 END) AS Y1980,
       SUM(CASE WHEN EXTRACT(YEAR FROM HIREDATE) = 1981 THEN 1 ELSE 0 END) AS Y1981,
       SUM(CASE WHEN EXTRACT(YEAR FROM HIREDATE) = 1982 THEN 1 ELSE 0 END) AS Y1982,
       SUM(CASE WHEN EXTRACT(YEAR FROM HIREDATE) = 1983 THEN 1 ELSE 0 END) AS Y1983
FROM EMPLOYEE;
```

### Output

| TOTAL_EMP | Y1980 | Y1981 | Y1982 | Y1983 |
| --------- | ----- | ----- | ----- | ----- |
| 14        | 1     | 10    | 2     | 1     |

---

## Question 7

Get the last Sunday of any month.

### Query

```sql
SELECT NEXT_DAY(LAST_DAY(SYSDATE) - 7, 'SUNDAY') AS LAST_SUNDAY
FROM DUAL;
```

### Output

| LAST_SUNDAY |
| ----------- |
| 29-MAR-2026 |

---

## Question 8

Display department numbers and total number of employees in each department.

### Query

```sql
SELECT DEPTNO, COUNT(*) AS TOTAL_EMPLOYEES
FROM EMPLOYEE
GROUP BY DEPTNO;
```

### Output

| DEPTNO | TOTAL_EMPLOYEES |
| ------ | --------------- |
| 10     | 3               |
| 20     | 5               |
| 30     | 6               |

---

## Question 9

Display various jobs and total number of employees in each job group.

### Query

```sql
SELECT JOB, COUNT(*) AS TOTAL_EMPLOYEES
FROM EMPLOYEE
GROUP BY JOB;
```

### Output

| JOB       | TOTAL_EMPLOYEES |
| --------- | --------------- |
| CLERK     | 4               |
| MANAGER   | 3               |
| SALESMAN  | 4               |
| ANALYST   | 2               |
| PRESIDENT | 1               |

---

## Question 10

Display department numbers and total salary for each department.

### Query

```sql
SELECT DEPTNO, SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE
GROUP BY DEPTNO;
```

### Output

| DEPTNO | TOTAL_SALARY |
| ------ | ------------ |
| 10     | 8750         |
| 20     | 10875        |
| 30     | 9400         |

---
