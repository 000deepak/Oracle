### Diff between sql & oracle
- INSERT MULTIPLE ROWS
- AUTOINCREMENT
- LIMIT


### create
```sql
CREATE TABLE employees (
id INT NOT NULL PRIMARY KEY,
first_name VARCHAR2 (255) NOT NULL,
last_name VARCHAR2 (255) NOT NULL,
age INT NOT NULL,
current status VARCHAR2 (255) DEFAULT 'employed' NOT NULL);
```

### insert
```sql
INSERT INTO employees (id, first_name, last_name, age) VALUES
(1, 'Dora', 'Smith', 58);
INSERT INTO employees (id, first_name, last_name, age) VALUES
(2, 'Eora', 'Imith', 60);
```

### update
```sql
update employees set age = 89 where id = 1;
```

### drop
```sql
drop table employeesd;
```

### read
```sql
select from employees;
```

### distinct
```sql
SELECT DISTINCT first name FROM employees;
SELECT DISTINCT first_name, last_name FROM employees;
```

### Order
```sql
SELECT first_name FROM employees ORDER BY first_name;
```
### Limit
```sql
SELECT first_name FROM employees LIMIT 1;
```
### llg
```sql
SELECT first_name FROM employees where rownum <2;
```
### Like
```sql
SELECT first_name FROM employees WHERE first_name LIKE 'Doral';
```
### Count
```sql
SELECT COUNT(*) FROM employees;
```
### GROUP BY: aggregates identical data into single rows
```sql
SELECT first_name FROM employees GROUP BY first_name;
```
### MIN: return minimum column value
```sql
SELECT MIN (age) FROM employees;
```
### MAX: return maximum column value
```sql
SELECT MAX (age) FROM employees;
```
### MAX/MIN with GROUP BY Group row first before finding minimum
```sql
SELECT age,
MIN (age)
FROM employees
GROUP BY age;
```
```sql
### SUM: sum column value
SELECT age, SUM (age)
FROM employees
GROUP BY age;
```