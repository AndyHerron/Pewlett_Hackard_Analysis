# Pewlett-Hackard employee database analysis

## Overview of analysis
Pewlett-Hackard is a huge company with a large number of employees who are about to reach retirement eligibility.  Company management has tasked us to compile some lists of data that will help them deal with that situation.  They need to know how many employees are about to retire and from which departments, so that they may determine how to best move forward with replacing those employees.


### Resources
* Data Sources: departments.csv, dept_manager.csv, dept_emp.csv, employees.csv, salaries.csv, titles.csv
* Software: pgAdmin 4, PostgreSQL, QuickDataBaseDiagrams.com
![flowchart of databases](https://github.com/AndyHerron/Pewlett_Hackard_Analysis/blob/main/EmployeeDB2.png.png)

## Results

### Highlight four major points from the analysis

1. *About 1/4 of all Pewlett-Hackard employees will be retiring.* Assuming that Pewlett-Hackard will want to stay somewhat close to their current staffing levels, they have to 
	embark on a huge hiring spree. The sheer numbers of people who will be leaving will result in huge turnover in their company, and any dramatic drop in 
	employee numbers could have a devastating effect on their business.
 
2. *Most of the employees retiring are in senior positions.* Not only are large numbers of people leaving, but most of those who are retiring are either senior engineers or
	senior staff members.  That could potentially deal a serious blow to the knowledge base of the company.  The overall experience of those people will be impossible
	to replace in the short term and will take time to build back up.
![retiring employees by title](https://github.com/AndyHerron/Pewlett_Hackard_Analysis/blob/main/count_of_titles.png)

3. *Pewlett-Hackard is considering implementing a mentorship program* We were tasked to see how many current employees would be eligible for the mentorship program and 
	to be eligible, the employee must have been born in 1965.  There are currently 1549 employees who would be eligible for the program.

4.  *The mentorship program should be expanded.*  There's no reason to limit the participation of employees in the mentorship program to just people born in 1965.  The criteria
	for allowing people to join should be expanded.  
`-- Challenge deliverable #2.
-- Create a Membership Eligibility table.
SELECT DISTINCT ON (e.emp_no)
	e.emp_no,
	e.first_name,
	e.last_name,
    e.birth_date,
    de.from_date,
    de.to_date,
	t.title
INTO mentorship_eligibility
FROM employees as e
INNER JOIN dept_emp as de
ON (e.emp_no = de.emp_no)
INNER JOIN titles as t
ON (e.emp_no = t.emp_no)
WHERE (e.birth_date BETWEEN '1965-01-01' AND '1965-12-31')
     AND (de.to_date = '9999-01-01')
ORDER BY emp_no;`

## Summary: Provide high-level responses to the following questions, then provide two additional queries or tables that may provide more insight into the upcoming "silver tsunami."

### How many roles will need to be filled as the "silver tsunami" begins to make an impact?
<<<<<<< HEAD
	It is unclear from the information that we have been provided as to how soon the employees in question will actually retire.  It will likely be spread out over several years, 
but that is good because it will give management more time to react and implement their plans to bring on new staff.  The number of employees who were born from 1952 through 1955 is
approximately one-fourth of their total number of employees.  There are over 75,000 employees who were born from January 1, 1952 through December 31, 1955.  The number of total employees
in the 'employees.csv' database is 300,024.

### Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
	Based upon the numbers that we've already determined, there are only 1,549 current employees eligible for the mentorship program and more than 75,000 who are leaving.  That's way more potential
teachers than students.  The number of 'mentees' should be significantly increased to try to retain as much of the company's knowledge base as possible.  Every retiring employee who walks out the 
door without doing some type of mentorship is an opportunity lost.
=======
It is unclear from the information that we have been provided as to how soon the employees in question will actually retire.  It will likely be spread out over several years, 
but that is good because it will give management more time to react and implement their plans to bring on new staff.  The number of employees who were born from 1952 through 1955 is approximately one-fourth of their total number of employees.  There are over 75,000 employees who were born from January 1, 1952 through December 31, 1955.  The number of total employees in the 'employees.csv' database is 300,024.

### Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
Based upon the numbers that we've already determined, there are only 1,549 current employees eligible for the mentorship program and more than 75,000 who are leaving.  That's way more potential teachers than students.  The number of 'mentees' should be significantly increased to try to retain as much of the company's knowledge base as possible.  Every retiring employee who walks out the door without doing some type of mentorship is an opportunity lost.
>>>>>>> e1380e333da45b5650ac5ce9ba55883290b90dd6
