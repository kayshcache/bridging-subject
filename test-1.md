# Database Systems Bridging Course
Student number:
Student name:
# Sample Test 1
## Question 1
Some questions to clarify answers:

## Question 2
As this is explicitly "data definition statements"... These statements are those to be added to the `CREATE TABLE` statement.
1. Add to the `CREATE TABLE TRIP` statment:
```sql
TLENGTH INTEGER NOT NULL, /* Length of a trip */
  CONSTRAINT trip_check1 CHECK (TLENGTH BETWEEN 0 AND 10000)
```
2. Include a new definition statement for a courses table:
```sql
CREATE TABLE COURSE(
  course_title VARCHAR(255) NOT NULL,
  conducted_date DATE NULL,
    CONSTRAINT course_pkey PRIMARY KEY (course_title, conducted_date),
    CONSTRAINT course_fkey1 FOREIGN KEY (course_title) REFERENCES EMPLOYEE (ENUM)
);
```
3. ```sql
CREATE TABLE SKILL(
  skill_name VARCHAR(30) NOT NULL,
    CONSTRAINT skills_pkey PRIMARY KEY (skill_name),
    CONSTRAINT skills_fkey1 FOREIGN KEY (skill_name) REFERENCES EMPLOYEE(ENUM) ON DELETE CASCADE
);
```
4. New definition statement for TRUCK table
 ```sql
CREATE TABLE TRUCK( /* Descriptions of trucks */
  REGNUM VARCHAR(10) NOT NULL, /* Registration number */
  CAPACITY DECIMAL(7) NOT NULL, /* Capacity of a truck */
  WEIGHT DECIMAL(5) NOT NULL, /* Weight of a truck */
  STATUS VARCHAR(10) NOT NULL, /* Added for keeping status */
    CONSTRAINT TRUCK_PKEY PRIMARY KEY(REGNUM),
    CONSTRAINT STATUS_check1 CHECK (STATUS IN ("available", "used", "maintained")
);
## Question 3
1. A driver with a license number 101 used a truck with a registration PKR856 to perform a trip on 15 April 2016. A driver first travelled from Sydney to Goulburn. Then, the driver travelled from Goulbourn to Waga Waga and then, finally to Melbourne. Assume that information about the driver and the truck used is already recorded in the database and that the largest number of a trip is 500.
I'm assuming the TNUM autoincrements?
```sql
INSERT INTO TRIP(LNUM, REGNUM, TDATE)
  VALUES(101, "PKR856", 2016-04-15);
  
```
2. "Information about a trip number 200 must be removed from the database together with information about all legs of the trip. Note, that a foreign key TRIPLEG_FKEY1 does not have ON DELETE
CASCADE clause!"
```sql
DELETE FROM TRIPLEG WHERE TNUM = 200;
DELETE FROM TRIP WHERE TNUM = 200;
```
3. Information about all registration numbers and capacities of all trucks that performed at least one trip in 2015 must be copied to a new relational table TRUCK2015. There is no need to enforce any consistency constraints on the new table and there is no need to delete such information from a relational table TRUCK.
```sql
```
4. A driver that has a driver license number 102 decided to leave the company. Information about the driver must be removed from the database. Information about the trips performed by the driver must be left in the database without a driver license number.
HOW: The LNUM field is `NOT NULL` - How can I update the records in TRIP to be without a driver license number.
```sql
``` 
SELECT DEPARTMENT.code, COURSE.cnum, title
FROM DEPARTMENT JOIN COURSE ON DEPARTMENT.name = COURSE.offered_by
WHERE credit = 6;

SELECT * FROM COURSE
WHERE offered_by IN (SELECT name FROM DEPARTMENT WHERE chair = 'JB');
## QUESTION 4
Write SELECT statements that implement the following queries.
1. Find the first and the last names of all drivers who used a truck with a registration number PKR856 at least one time.

```sql
SELECT FNAME, LNAME
FROM EMPLOYEE 
WHERE REGNUM = "PKR856"

select ENUM from DRIVER join TRIP on DRIVER.LNUM = TRIP.LNUM
WHERE TRIP.REGNUM = "PKR856";

JOIN (SELECT LNUM FROM TRIP WHERE REGNUM = "PKR856") TRIP
ON  
```
2. Find the first and the last names of all drivers who never used a truck with a registration number PKR856.
3. Find the first and the last names of all drivers who used a truck with a registration number PKR856 at least three times.
4. Find the first and the last names of all drivers who used a truck with a registration PKR856 and who used a truck with a registration AL08UK on two different trips.
5. Find the driver license number for all drivers together with the total number of trips performed by each driver. If a driver performed no trips so far then list his driver license number with 0 (zero).
# Sample Test 2
## Question 1
R (A, B, C, D, E, F)
A --> C
C --> D
E, F --> A
## Question 2
Write the data definition statements of SQL that modify the structures of a database listed on a page 1 of the
test paper such that:
1. It should be possible, after a modification, to add to the database information about commission
percentage for each employee. The value of commission percentage is between 0 and 1. For example,
0.45 represents 45%.
2. It should be possible, after a modification, to add information that a department manager is an employee
and a manager of an employee is an employee as well.
3. It should be possible, after a modification, to store information about the historical salaries of employees
in a relational table JOBHISTORY. Additionally, a modification must enforce a constraint such that the
end of job date must be later than the start of job date for employees in the relational table
JOBHISTORY.
4. A modification must delete an attribute (a column) hire_date from a relational table EMPLOYEE.
Additionally a modification must enforce a constraint such that all values of attribute salary in a
relational table EMPLOYEE must be a positive.
## Question 3
Write the data manipulation statements of SQL that modify the contents of a database listed on page 2 of the test paper in the ways described below. Note, that you are not allowed to modify and/or to drop any consistency constraints.
1. James Bound, employee id 007, phone number 123.456.7890 has been hired on 5 March 2012
as a Stock Manager. His email is jamesbound2012@gmail.com and his salary is 8000. He works
in ta department of Marketing and his manager id is 201.
2. Information about an employee number 105 must be removed from the database together with
information about the employee’s job history. Note, that a foreign key JOBHISTORY_FK2 does not have
ON DELETE CASCADE clause. Also assume that the employee is not a manager.
3. A department Human Resources has been moved to a new location. The new address is 100
Century Avenue, Shanghai, China. Post code is 200120.
4. A department Shareholder Service has been renamed to Share Service. Update all related
data in the database.
## Question 4
Write SELECT statements that implement the following queries.
1. Find the full names of employees who are the topmost level managers, i.e. who are not managed by
any other employee.
2. List the full names of all departments and full names of employees working in each department. The results should be displayed in the descending order of department names and the full names of
employees from the same department must be listed in the ascending order of the last names.
3. Find the full names of employees who work in a city Geneva in Switzerland.
4. Find the names of departments, names of countries and total number of employees for each
department that hires more than 5 employees.
5. Find the employee id, first name and last name for each employee who is directly managed by
Matthew Weiss.
