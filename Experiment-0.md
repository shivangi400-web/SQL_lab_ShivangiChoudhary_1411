# SQL Lab – Experiment 0

## Aim

| Description |
|------------|
| To understand the database schema, table structures, and sample data used in all SQL lab experiments. |

---

# Table 1: EMPLOYEE

## Column Description

| Column Name | Data Type | Size | Constraints | Description |
|------------|----------|------|------------|-------------|
| EMPNO | NUMBER | 4 | PRIMARY KEY | Employee Number (Unique ID) |
| ENAME | VARCHAR2 | 20 | NOT NULL | Employee Name |
| JOB | VARCHAR2 | 20 | - | Job Title |
| MGR | NUMBER | 4 | - | Manager Employee Number |
| HIREDATE | DATE | - | - | Date of Hiring |
| SAL | NUMBER | 10 | - | Monthly Salary |
| COMM | NUMBER | 7 | - | Commission Amount |
| DEPTNO | NUMBER | 2 | FOREIGN KEY | Department Number |

---

## Employee Table Data

| EMPNO | ENAME | JOB | MGR | HIREDATE | SAL | COMM | DEPTNO |
|------|------|------|------|----------|------|------|--------|
| 7369 | SMITH | CLERK | 7902 | 17-Dec-80 | 800 | - | 20 |
| 7499 | ALLEN | SALESMAN | 7698 | 20-Feb-81 | 1600 | 300 | 30 |
| 7521 | WARD | SALESMAN | 7698 | 22-Feb-81 | 1250 | 300 | 30 |
| 7566 | JONES | MANAGER | 7839 | 02-Apr-81 | 2975 | - | 20 |
| 7654 | MARTIN | SALESMAN | 7698 | 28-Sep-81 | 1250 | 1400 | 30 |
| 7698 | BLAKE | MANAGER | 7839 | 01-May-81 | 2850 | - | 30 |
| 7782 | CLARK | MANAGER | 7839 | 09-Jun-81 | 2450 | - | 20 |
| 7788 | SCOTT | ANALYST | 7566 | 09-Dec-82 | 3000 | - | 40 |
| 7839 | KING | PRESIDENT | - | 17-Nov-81 | 5000 | - | 20 |
| 7844 | TURNER | SALESMAN | 7698 | 08-Sep-81 | 1500 | 0 | 30 |
| 7876 | ADAMS | CLERK | 7788 | 12-Jan-83 | 1100 | - | 20 |
| 7900 | JAMES | CLERK | 7698 | 03-Dec-81 | 950 | - | 30 |
| 7902 | FORD | ANALYST | 7566 | 03-Dec-81 | 3000 | - | 20 |
| 7934 | MILLER | CLERK | 7782 | 23-Jan-82 | 1300 | - | 10 |

---

# Table 2: DEPARTMENT

## Column Description

| Column Name | Data Type | Size | Constraints | Description |
|------------|----------|------|------------|-------------|
| DEPTNO | NUMBER | 2 | PRIMARY KEY | Department Number |
| DNAME | VARCHAR2 | 15 | NOT NULL | Department Name |

---

## Department Table Data

| DEPTNO | DNAME |
|--------|-------|
| 10 | RESEARCH |
| 20 | ACCOUNTING |
| 30 | SALES |
| 40 | OPERATIONS |

---

# Key Relationships

| Relationship | Description |
|-------------|------------|
| EMPLOYEE.DEPTNO → DEPARTMENT.DEPTNO | Foreign Key |
| EMPLOYEE.MGR → EMPLOYEE.EMPNO | Self Reference |

---

# Hierarchy

| Employee | Role |
|----------|------|
| KING | President (No Manager) |
| JONES, BLAKE, CLARK | Report to KING |
| SCOTT, FORD | Report to JONES |
| SMITH, ADAMS | Report to FORD/SCOTT |
| Others | Report to BLAKE |

---

# Employee Statistics

| Metric | Value |
|-------|------|
| Total Employees | 14 |
| Total Salary Paid | 29,025 |
| Average Salary | 2,073.21 |
| Highest Salary | 5000 (KING) |
| Lowest Salary | 800 (SMITH) |

---

# Department Statistics

| Department | DEPTNO | Employees | Avg Salary |
|------------|--------|-----------|-----------|
| RESEARCH | 10 | 1 | 1300 |
| ACCOUNTING | 20 | 5 | 2685 |
| SALES | 30 | 6 | 1483.33 |
| OPERATIONS | 40 | 1 | 3000 |

---

# Job Distribution

| Job | Count | Avg Salary |
|-----|------|-----------|
| CLERK | 4 | 1087.50 |
| SALESMAN | 4 | 1400 |
| MANAGER | 3 | 2758.33 |
| ANALYST | 2 | 3000 |
| PRESIDENT | 1 | 5000 |

---

# Setup Instructions

| Step | Description |
|------|------------|
| Step 1 | Create DEPARTMENT table |
| Step 2 | Insert Department Data |
| Step 3 | Create EMPLOYEE table |
| Step 4 | Insert Employee Data |
| Step 5 | Verify Data |

---

# Important Notes

| Topic | Description |
|------|------------|
| NULL in MGR | Top-level employee (KING) |
| NULL in COMM | No commission |
| Commission | Only SALESMAN earn |
| Salary Range | 800 – 5000 |
| Hire Dates | 1980 – 1983 |

---

# Summary

| Points |
|--------|
| Table schemas |
| Sample data |
| Relationships |
| Statistics |
| Setup instructions |
| Query reference |