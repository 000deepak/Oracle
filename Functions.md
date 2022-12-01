# Functions
Functions are used to solve particular task and also functions must return a value. 
* Oracle have two types of functions. 
1.	Predefined functions 
2.	User defined functions 


## 1) Predefined functions: there are 4 types. 
*	Number function 
*	Character function 
*	Date function 
*	Group function(or) Aggregate function

### 1) Number function: 
These functions operate over “number” data. 
*	Abs() : It is used to convert negative values into positive values.
```sql 
SQL> select  abs(-50) from dual; 
50 
```
*	Dual(): Dual is a predefined virtual table which contains only one row and one column Dual table is used to test predefined, user defined functions functionality. 
```sql 
SQL> select nvl(null,30) from dual; 
30 
SQL> select nvl(20,30) from dual; 
20 
```
> Note: In oracle by default dual table column datatype is varchar2().

•	Mod(m,n): It will gives remainder after „m‟ divided by „n‟. 
```sql  
Eg: SQL> select mod(10,5) from dual; 
0
``` 
*	Round(m,n): It rounds given floated valued number „m‟ based on „n‟.
```sql  
Eg: SQL> select round(1.8) from dual; 
2 
SQL> select round(1.23456,3) from dual; 
1.235
``` 
> Note: Round always checks remaining number if remaining number is above 50% then one added to the rounded number. 

*	Trunc(m,n): It truncates given floated values number „m‟ based on „n‟. This function doesn‟t check remaining number is above 50% or below 50%.
```sql  
Eg: SQL>select trunk(1.8) from dual; 
Eg: SQL> select trunk(1.23456,3) from dual; 
1.234
``` 
* Greatest(exp1,exp2,…. expn)
* Least(exp1,exp2,…. expn): 
Greatest returns maximum value among given expressions. Where as Least returns minimum value among given expressions. 
```sql 
SQL> select greatest(3,5,8,9) from dual ; 
9 
SQL> select ename, sal, comm, greatest(sal,comm)from emp where comm is not null; 
SQL> select max(sal) from emp; 
6600 
``` 
 
* Ceil() : returns nearest greatest integer
* Floor() : returns nearest lowest integer
* These two functions always  return integer. 
```sql  
select ceil(1.3) from dual; 
2 
select floor(1.9) from dual; 
1 
```

### 2) CHARCTER FUNCTIONS: 
•	Upper(): It is used to convert a string or column values into “ upper case “. Eg: select upper(„abc‟) from dual; 
ABC 
For column: SQL> select upper(ename) from dual; 
•	Lower():  
Eg: select lower(ename) from emp; 
Updating or modifying data within table: 
SQL> update emp set ename=lower(ename); 
•	Initcap(): It returns first letter is capital and all remaining letters are small. 
Eg: SQL> select initcap(ename) from emp; 
Eg: SQL> select initcap(„ab cd ef‟) from emp; Ab Cd Ef 
•	Length(): It returns number datatype that is ., it returns total length of the string including spaces. 
Eg: select length(„AB_CD‟) from dual; 5 
 	Substr(): It will extract portion of the string within given string based on last two parameters. 
Eg: select substr(„ABCDEF‟,2,3) from dual; 
BCD 
SQL> select substr(„ABCDEF‟,-2,3) from dual; 
EF 
SQL> select substr(„ABCDEF‟,-4) from dual; 
CDEF 
Syntax: substr(columnname (or) „string name‟, starting position, no. of characters position); 
Starting position-> can be +ve or –ve 
Starting position and no. of characters position-> must be numbers 
 
Q) write a query to display the employees whose ename second letter would be “LA” from emp table using substring function? 
And: SQL> select * from emp where substr(ename,2,2)=‟LA‟; 
BLAKE 
CLARK 
Note: In all database systems we are not allowed to use group functions in where clause but we are allowed to use number functions, character functions, date functions in where clause. Eg: select * from emp where sal=max(sal); Error: group function is not allowed here. 
Q) write a query to display the employee whose employees length is 5 from emp table. Ans: SQL> select * from emp where length(ename)=5; 
 
* Instr(): instr() always returns number datatype that is it returns position of the delimiter, position of the character, position of the string within given string . Eg: SQL> select instr(„ABC*D‟,‟*‟) from dual; 
 
Date: 19/3/15 
Eg: SQL> select instr(„ABCDEFGHCDKMNHCDJL‟,‟CD‟,-5,2) from dual; 
      3 
SQL> select instr(„ABCDEFGHCDKMNHCDJL‟,‟CD‟,-4,2) from dual; 
   9 
Syntax: instr(columnname(or)‟string name‟, „str‟, searching position, No. of occurrences from searching position); 
Searching position -> +ve or –ve  
Searching and No. of occurrences -> must be numbers. 
Always in string returns position based on last two parameters but oracle server counts no. of characters left side first position onwards. 
 
Lpad(): It will fills remaining spaces with specified character on the left side of the given string. Here always second parameter returns total length of the string. And also third parameter is an optional.Syntax: Lpad(columnname (or) „string name‟, total length, „filled character‟); 
Total length -> number 
 
Eg: SQL> select lpad(„ABCD‟,10,‟#‟) from dual; 
######ABCD 
SQL> select lpad(„ABC‟,5) from dual; 
 (space)(space)ABC 
SQL> select lpad(„ABC‟,2,‟*‟) from dual; 
AB 
 
Rpad(): 
Eg: SQL> select rpad(„ABCD‟,10,‟#‟)from dual; 
ABCD###### 
SQL> select rpad(ENAME,50,‟-„)||sal from emp; 
 
Ltrim: It removies specified character on the left side of the given string. 
Syntax: Ltrim(columnname(or)‟string name‟, {set of characters}); 
 
Eg: SQL> select ltrim(„SSMISSTHSS‟,‟S‟)from dual; 
 MISSTHSS 
SQL> select job,ltrim(job,‟CSM‟) from emp; 
    JOB                               LTRIM(JOB) 
-----------------          ------------------------- 
CLERK                               LERK 
SALESMAN                         ALESMAN 
MANAGER                          ANAGER 
 
Rtrim:  
Eg: SQL> select rtrim(„SSMISSTHSS‟,‟S‟) from dual; 
SSMISSTH 
Trim(): Oracle 8i introduced trim function it is used to remove left and right side specified characters and also it is used to remove leading and trailing spaces. 
Syntax: trim(„character‟ from „string name‟); 
Eg: SQL> select trim(„S‟ from „SSMISSTHSS‟)from dual; 
MISSTH 
This function also behaves like a ltrim, rtrim based on leading and trailing claused. Eg: select trim(leading „s‟ from „SSMISSTHSS‟) from dual; 
SSMISSTH 
Eg: select length(trim(„   welcome   „))from dual; 
7 
 
Translate() and Replace(): 
Translate() is used to replaces character by character where as replace() is used to replaces character by string (or) string by string. 
 
Eg: select translate(„india‟,‟in‟,‟xy‟),replace(„india‟,‟in‟,‟xy‟) from dual; 
 
Translate                             Replace 
Xydxa                                  xydia 
 
Syntax: translate(„str1‟,‟str2‟,‟str3‟….); 
Eg: select translate(„ABCDEF‟,‟FEDCBA‟,123456); 
654321 
Eg: select replace(„ABC‟,‟ „,‟india‟)from dual; 
AindiaBindiaC 
Eg: select job,replace(job, „SALESMAN‟,‟MARKETING‟) from emp; 
Note: In replace function if we are not specifying third parameter specified character permanently removed from the string. 
Eg: select replace(„SSMISSTHSS‟,‟S‟) from dual; 
MITH 
 
Date: 20/3/15 
If you want to count number of times particular character occurs within a given string then also we are using replace function along with length function. 
Q) Write a query to count number of times that particular „I‟ occurred within given string „india‟ using replace function? 
Ans: SQL> select length(„india‟)-length(replace(„india‟,‟I‟)) from dual; 
        2 
Concat(): It is used to concatenate given two strings. 
Eg: select concat(„wel‟,‟come‟)from dual; 
Welcome 
 
DATE functions: In oracle by default date format is DD-MON-YY. Oracle having following date functions. 1. Sysdate 
2.	Add_months() 
3.	Last_day() 
4.	Next_day()
5.	Months_between() 
 
1)	Sysdate: It returns current date of the system in the oracle date format  
SQL> select sysdate from dual; 
 20-MAR-15 
2)	Add_months(): It is used to add or subtract number of months to the specified date based on second parameter. 
Syntax: add_months(date, number); 
Number-> can be positive or negative. 
Eg: SQL> select add_months(sysdate,1)from dual; 
20-Apr-15 
SQL> select add_months(sysdate,-1) from dual; 
20-FEB-15 
3)	Last_day(): It returns last date of the given months based on the passed date. This function always accepts one parameter. 
Syntax: last_day(date); 
Eg: SQL> select last_day(sysdate)from dual; 
31-Mar-15 
4)	Next_day(): It returns next occurrence day from the specified date based on second parameter. 
Syntax: next_day(date,‟day‟); 
Eg: select next_day(sysdate,‟monday‟)from dual; 
23-MAR-15 
5)	Months_between(): These function always returns “number” data type. i.e., it returns number of months between two specified dates. 
Syntax: months_between(date1,date2) 
Here date1 is more than date2 otherwise this function returns “negative” sign. 
Eg: SQL> select ename, round(months_between(sysdate,hiredate))from emp; 
 
DATE arithmetic: 
1.	Date + number 
2.	Date – number 
3.	Date1 + date2 
4.	Date1 – date2 
Eg: SQL> select sysdate+1 from dual; 
SQL> select sysdate-1 from dual; 
SQL> select sysdate-sysdate from dual; 
   0 
Q) write a query to display first date of the current month using predefined date functions sysdate, add_months(), last_date() functions. 
Ans: SQL> select last_day((add_months(sysdate,-1)))+1 from dual; 
                          OR 
SQL> select add_months(last_day(sysdate),-1)+1 from dual; 
01-MAR-15 
 
DATE CONVERSION FUNCTIONS: 
Oracle provided two date conversion function. They are: 
1.	To_char() 
2.	To_date() 
 
Date: 23/3/15 
 
1. to_char(): It is used to convert date time into character type i.e., it converts date type into date string. 
Eg: SQL> select to_char(sysdate,‟dd/mm/yy‟)from dual; 
23/03/15 
Note: Basically “to_char” character formats are case sensitive formats. 
Eg: SQL> select to_char(sysdate,‟DAY‟)from dual; 
MONDAY 
Day-> Monday(lowercase letters) 
DAY 
DY 
MONTH 
MON 
YEAR 
RETURNS CHARACTER AS OUTPUT 
D 
DD 
DDD 
MM 
YY 
YYYY 
HH 
MI 
SS 
RETURNS NUMBER AS OUTPUT 
Eg: SQL> select to_char(sysdate,‟DY‟)from dual; 
MON 
 
Eg: SQL> select to_char(sysdate,‟D‟)from dual; 
2 
D->day of the week(sun-1,mon-2,tue-3,….sat-7) 
DD->day of the month 
DDD->day of the year(tells how many days completed) 
DDTH-> used as date with „rd‟ or „th‟ (eg: 5th 19th 23rd) 
Eg: SQL> select to_char(sysdate,‟DDSPTH‟)  from dual; 
Twenty third 
SP-> spell out
Eg: SQL> select to_char(sysdate,‟MON‟) from dual; 
MAR 
Eg: SQL> select to_char(sysdate,‟HH:MI:SS‟) from dual; 
09:51:42 
By default 12-hours format  to convert into 24-hours format we have to  “HH24:MI:SS” (24-hours format) 
 
Q) SQL> select to_char(‟15-JUN-05‟,‟15-JUNE-05‟) from dual; 
Error: invalid number 
Note: whenever we are using to_char() always first parameter must be oracle “date” type otherwise oracle server returns an error. 
 
2. to_date(): It is used to convert date string into oracle “date” type(oracle date format) 
Eg: SQL> select to_date(‟27/JUNE/05‟) from dual; 
27-JUN-05 
Eg: SQL> select to_date(„27/06/05‟) from dual; 
Error: invalid month (or) not a valid month 
Whenever are using to_date() passed parameter return values match with the default date format return values. Otherwise oracle server returns an error. To overcome this problem use a second parameter as same as first parameter format then only oracle server automatically converts “date string” into “date type”. 
Solution: SQL> select to_date(‟27/06/05‟,‟DD/MM/YY‟) from dual; 
27-JUN-05 
 
*	SQL> select to_date(‟09-feb-15‟)+5 from dual; 14-feb-15 
*	SQL> select to_date(‟09-feb-15‟,‟DD-MM-YY‟)+5 from dual; 14-FEB-15 
Q) Write a query to convert given date string into client requirement format using to_char() Given date is -> ‟15-jun-05 
Expected format-> „15/jun/05‟ 
SQL> select to_char(‟15-jun-05‟,‟dd/month/yy‟) from dual; 
Error: invalid number 
SQL> select to_char(to_date(‟15-jun-05‟),‟dd/month/yy‟) from dual; 
15/jun         /05 
Date: 24/3/15 
 
Fill mode(FM): Whenever we are using to_char() if format is either month(or) day then oracle server automatically returns “spaces” when the month (or) day value less than the maximum length of the month (or) day. To overcome this problem oracle provided Fill Mode(FM) which suppress blank spaces and leading zeros(0). This mode is used in second parameter of the to_char(). 
Eg: SQL> select to_char(to_date(‟15-JUN-05‟),‟DD-MON-YY‟) from dual; 
15-JUNE       -05 
SQL> select to_char(to_date(‟15-JUN-05‟), „DD/FMMONTH/YY‟) from dual; 
15/JUNE/05 
Q) Write a query to display the employees who are joining in the month December from “emp” table using to_char()? 
Ans: SQL> select * from emp where to_char(HIREDATE,‟MON‟)= „DEC‟; 
                                    OR 
SQL> select * from emp where to_char(HIREDATE,‟MM‟)=‟12‟; 
                                    OR 
SQL> select * from emp where to_char(HIREDATE,‟FMMONTH‟)=‟DECEMBER‟; 
 
Q) Write a query to display the employees who are joining in the year „81‟ from emp table using to_char()? 
Ans: SQL> select * from emp where to_char(hiredate,‟yy‟)=‟81‟; 
SQL> select hiredate, to_char(hiredate,‟yyyy‟) from emp; 
In Oracle, whenever we are passing date string into date functions then oracle server automatically converts date string into date type. Eg: SQL> select last_day(‟12-JUN-05‟) from dual; 
30-JUN-05 
But here passed parameter format must be default date format otherwise oracle server returns an error. To overcome this problem we must use to_date(). 
Eg: SQL> select last_day(„12-06-05‟) from dual; 
Error: invalid month 
Solution: SQL> select last_day(to_date(‟12-06-05‟,‟DD-MM-YY‟)from dual; 
30-JUN-05 
In Oracle whenever we are inserting dates into date data type column then oracle server automatically converts date string into date type when inserted date string is in oracle date format. Otherwise oracle server returns an error. To overcome this problem also then we must use to_date(). 
Eg: SQL> create table test(col1 date); 
SQL> insert into test values(sysdate); 
SQL> select * from test; 
    COL1 
------------ 
24-MAR-15 
SQL> insert into test values(‟15-aug-05‟); 
SQL> select * from test; 
    COL1 
------------ 
24-MAR-15 15-AUG-05 
SQL> insert into test values(‟15-08-05‟); 
Error: not a valid month 
SQL> insert into test values(to_date(‟15-08-05‟,‟DD-MM-YY‟)); 
1 row inserted
SQL> select * from test; 
    COL1 
------------ 
24-MAR-15 
15-AUG-05 
15-AUG-05 
 
Round(), Trunc() used in dates: 
In Oracle, “date” data type contains both date and time. Whenever we are using the round() or trunc() then automatically date part changed based on time portion. 
 
Date: 25/3/15 
 
Round() adds one day to the given date if time portion is greater than or equal to 12 noon and also time portion automatically set to “zero”. 
Eg: SQL> select to_char(sysdate,‟DD-MON-YYYY HH24:MI:SS‟) from dual; 25-MAR-2015   12:24:59 When applying round(): 
SQL> select to_char(round(sysdate),‟DD-MON-YYYY HH24:MI:SS‟) from dual; 
26-MAR-2015  00:00:00 
Whenever we are using trunc() oracle server automatically returns same date if time portion is greater than or equal to 12 noon also and also trunc() time portion is set to “zero”(0) 
Eg: SQL> select to_char(trunc(sysdate),‟DD-MON-YYYY HH24:MI:SS‟) from dual; 
25-MAR-2015  00:00:00 
Q) Write a query to display the employees who are joining today from emp table? 
Ans: SQL> select insert into emp(empno,ename,hiredate)values(1, „MURALI‟,25-MAR-15); 
SQL> select * from emp; 
SQL> select * from emp where trunc(hiredate) = trunc(sysdate); 
 
GROUP FUNCTION (OR) AGGREGATE FUNCTION: 
Oracle having following group function 
1.	max() 
2.	min() 
3.	avg() 
4.	sum() 
5.	count(*) 
6.	count(column name) 
In all databases group functions are operate over number of values within a column and returns a single value 
1.	Max(): It returns maximum value within a column. 
Eg: SQL> select max(sal) from emp; 
6600 
SQL> select max(hiredate) from emp; 
23-MAY-87 
SQL> select max(ename) from emp; 
WARD     (A=1……… Z=26) 
 
2.	Min():  
Eg: SQL> select min(sal) from emp; 
750 
To know the senior most employee 
SQL> select min(hiredate) from emp; 
17-DEC-80 
In all database systems we are not allowed to use group functions in “where” clause. 
SQL> select * from emp where sal= min(sal); 
Error: group function is not allowed in “where” 
 
3.	Avg(): It returns average from number data type column. 
Eg: SQL> select avg(sal) from emp; 
2473.21429 
SQL> select avg(comm) from emp; 
550 
NOTE: In all database systems by default all group function ignores null values except “count(*)”. 
To count all null values also: 
SQL> select avg(nvl(comm,0)) from emp; 
157.142857 
 
4.	Sum(): It returns total from number data type column. 
Eg: SQL> select sum(sal) from emp; 
34625 
 
5.	Count(*): It counts number of rows in a table(including null values) 
Eg: SQL> select count(*) from emp; 
6.	Count(column name): It counts number of not null values within a column. 
SQL> select count(comm) from emp; 
4 
SQL> select count(distinct(dept no)) from emp; 
3 
GROUP BY: This clause is used to divide similar data items into set of logical groups. 
Syntax: select columnname….. from tablename group by columnname; 
 
Data: 26/3/15 
Q) Write a query number of employees in each department from emp table using “group by”? 
Ans: SQL> select deptno,count(*) from emp group by deptno; 
DEPTNO   COUNT(*) 
------- ---------- 
     30          6 
     20          5 
     10          3 
Q)  Write a query to display number of employees in each job from emp table using group by? 
Ans: SQL>  select job, count(*) from emp group by job; 
JOB         COUNT(*) 
--------- ---------- 
CLERK              4 
SALESMAN        4 
PRESIDENT       1 
MANAGER         3 ANALYST          2 
Q) Write a query to display deptno, minimum and maximum salary from emp using group by? 
Ans: SQL> select deptno, min(sal), max(sal) from emp group by deptno; 
DEPTNO   MIN(SAL)   MAX(SAL) 
------- ---------- ---------- 
     30        950       2850 
     20        800       3000 
     10       1300       5000 
 
Note: In all database systems we can also use “group by” clauses without using “group” functions. 
Eg: SQL> select deptno from emp group by deptno; 
RULE: Other than group function columns specified after select those all columns must be used in after “group by”. Otherwise  oracle server returns an error “not a GROUP BY expression”. 
Eg: SQL> select deptno, max(sal), ename from emp group by deptno,ename; 
ERROR at line 1: 
ORA-00979: not a GROUP BY expression 
 
SQL> select deptno from emp group by deptno,job; “Reverse also possible”. 
Note: Whenever we are submitting “group by” clauses then database servers select the data from the table from based on the group by clause columns. These columns space database servers group the data in the result set, from this result only we are selecting the data using number of columns after select keyword. 
Note: Whenever we are using group functions without using “group by” clause then database servers executes these group functions based on all values in a column. Whereas when we are using “group by” then these group functions executed each and every group wise in a table. Note: Generally in all database systems we are not allowed to display group function with another columns to overcome this problem we must use “group by” clause. Eg: step1: SQL> select sum(sal) from emp; 
34627 
Step2: SQL> select deptno, sum(sal) from emp; 
Error: not a single-group group function 
Solution: SQL> select deptno, sum(sal) from emp group by deptno; 
DEPTNO   SUM(SAL) 
------- ---------- 
     30       9400 
     20      10875 
     10       8750 
Eg: SQL> select deptno, job, sum(sal), count(*) from emp group by deptno, job; 
DEPTNO JOB         SUM(SAL)   COUNT(*) 
------- --------- ---------- ----------      20 CLERK           1900            2 
     30 SALESMAN        5600         4 
     20 MANAGER         2975          1 
     30 CLERK            950              1      10 PRESIDENT       5000          1      30 MANAGER         2850          1 
     10 CLERK           1300             1 
     10 MANAGER         2450          1 
     20 ANALYST         6000           2 
 
Date: 27/3/15 
 
Q) Write a query to display those departments having more than 3 employees from emp table? 
Ans: SQL> select deptno,count(*) from emp group by deptno where count(*)>3; Error: SQL commond not properly ended. 
Solution: SQL> select deptno, coutn(*) from emp group by deptno having count(*)>3; 
 
HAVING Clause: In all databse systems after “group by” clause we are not allowed to use “where” clause. In place of this one ansi/iso SQL provided another clause “having”. Generally if we want to restrict groups after “group by” then we must use “having” clause. Generally in “where” clause we are not allowed to use group functions where as in having clause we can also use group functions. 
Q) Write a query to display those departments having more than 10,000 sun(sal) from emp table? 
And: SQL> select deptno, sum(sal) from emp group by deptno having sum(sal)>10,000; 
 
 
Deptno      sum(sal) 
----------------------- 
  10          13550 
  20          12675 
 
Q) Write a query to display year, number of employees per year in which more than one employee was hired from emp table using “group by”? 
And: 	SQL> 	select 	to_char(hiredate,‟YYYY‟), 	count(*) 	from 	emp 	group by(to_char(hiredate,‟YYYY‟)); 
                                    OR 
SQL> select to_char(hiredate,‟YYYY‟) year, count(*) from emp  group by to_char(hiredate,‟YYYY‟)  having count(*)>1; 
 
year           count(*) 
------------------------ 
1981	10 
1982	2 
 
Invisible columns: 
Eg: SQL> select deptno, sum(sal) from emp  group by deptno  having sum(sal)>10000; 
Here count(*) is invisible column. 
SQL> select deptno, sum(sal) from emp 
Group by deptno  
Having count(*)>3; 
Deptno            sum(sal) 
--------------------------- 
  20  	12675 
  30  	 8400 
ORDER BY:  This clause is used to arrange the data in sorting order along with “order by” clause we are using two keywords. 
 
By default „order by‟ clause having “Ascending order”. 
Syntax: SQL> select * from tablename order by columnname[asc/desc]; 
Eg: SQL> select sal from emp order by sal; SQL> select deptno, sal from emp order by deptno, sal; 
Eg: SQL> select deptno, count(*) from emp Where sal>1000 group by deptno having count(*)>3 order by depnto desc; 
 
Deptno     count(*) 
---------------------- 
30 	 	4 
20 	 	5 
 
Date: 28/3/15 
 
Note: In oracle we can also use column position in place of columnname within “order by” clause which is used to improve performance query. 
Eg: SQL> select * from emp order by 6 desc; 
 
ROLLUP, Cube: 
Oracle 8i introduced rollup, cube clauses. These clauses are used along with group by clause only. These clauses are used to calculate subtotal, grand total automatically. Syntax: select col1, col2,…….. from tablename     group by rollup(col1,col2,..); 
Syntax: select col1, col2,…. From tablename group by cube(col1,col2,…); 
Rollup is used to calculate subtotal value based on a single column where as if we want to calculate subtotal value based on number of column wise then we must use cube. Eg: SQL> select deptno, job, sum(sal)from emp group by rollup(deptno, job); 
SQL> select deptno, job, sum(sal), count(*) from emp group by cube(deptno,job); 
Eg: SQL> select ename, sum(sal) from emp group by rollup(ename); 
