# Pewlett Hackard Analysis

## Overview
The purpose of this analysis is to help a fictitious company, Pewlett Hackard, prepare for the mass departure of retirement-ready employees, including some department managers and senior staff. This analysis makes use of an SQL database to supply an overview of,
1. Who may be leaving the company soon,
2. What positions these soon-to-be retirees currently hold,
3. How many employees hold these positions, and 
4. Who may be good cnadidates for specialized trainging to replace them. 

## Results
* A massive 72,458 current Pewlett Hackard employees will soon be eligible for retirment and may soon leave the company.

<img width="517" alt="UNIQUE_T_1" src="https://user-images.githubusercontent.com/114126935/202866473-e38cfb24-31ee-465d-ab2d-1c5ca143270e.png">

#### Note: In "Total rows" seen in the bottom left of the above image, the larger 72458 represents the total number of employees identified as reaching retirement age.

* Over 50,000 of these employees hold Senior Staff and Senior Engineer positions, and 2 of the employees are currently department managers. In addition to the more than 20,000 other employees preparing for retirement, this represents a major loss of leadership. 

<img width="308" alt="RET_EMP_1" src="https://user-images.githubusercontent.com/114126935/202866479-3ddda80e-8fc1-43a7-8e6c-3c5f3096fa07.png">

* Senior-level employees, Managers, and Technique Leaders may be excellent candidates to be mentors to the younger employees eligible for the mentorship program.

* A total of 1,549 current employees are eligible for the mentorship program. 

<img width="776" alt="MENT_ELG_1 ong" src="https://user-images.githubusercontent.com/114126935/202865979-57cc8de8-8c57-44af-9fec-897d090a8f86.png">

## Summary
If Pewlett Hackard is to replace empty roles on a 1:1 basis, the comapny will soon need to fill 72,458 roles. If every employee eligible for the mentorship program were to be promoted into new roles, that would still leave over 70,000 roles to fill. At a bare minimum, 2 managerial roles will need to be replaced, lest whole departments be left without managers. 

There are more than enough retirement-ready employees to mentor the mentorship-eligble employees. The company may even wish to expand the scope of the mentorship program in order to ensure that as much knowledge as possible is passed along to current employees and that the best, most highly-trained employees may be maintained. 

The following table, with query below, shows the total number of mentorship-eligible current employees per title and demonstrates that there are plenty of potential mentors available. 

<img width="301" alt="MENT_TITLE_1" src="https://user-images.githubusercontent.com/114126935/202866483-3fe4981a-b476-4182-911c-fd164d8f6f79.png">

`	SELECT COUNT(title) AS "Total Employees",
		title AS "Title"
	FROM mentorship_eligibilty
	GROUP BY title
	ORDER BY "Total Employees" DESC;`

The following table, with query below, shows that the company has 167,666 current employees born in 1956 or later (not part of the 'silver-tsunami'). 

<img width="418" alt="YNG_EMP_1" src="https://user-images.githubusercontent.com/114126935/202866967-3113c962-c784-4920-a790-7ed8bdb4a118.png">

`	SELECT DISTINCT ON (e.emp_no) e.emp_no,
		de.to_date,
		e.birth_date
	FROM employees AS e 
	LEFT JOIN dept_emp AS de
	ON (e.emp_no = de.emp_no)
	WHERE to_date = '9999-01-01'
	AND (e.birth_date > '1955-12-31')
	ORDER BY e.emp_no;`

With this many employees retained and over 70,000 employees soon to retire, it seems wasteful to mentor a mere 1,549 employees for leadership roles. This number makes up less than 1% of Pewlett Hackard's employees not-ready for ritrement. With so many employees eligible to become mentors, the company should consider opening the mentorship program to younger employees or employees who show outstanding performance or a special interest in the program. Perhaps menotors can be prompted to select employees they see as most likely to benefit from such a program. 
