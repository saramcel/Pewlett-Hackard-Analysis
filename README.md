# Pewlett Hackard Analysis

## Overview

### Purpose
We are preparing Bobby's boss at Pewlett-Hackard a dossier of employees who are retiring and those who might be promoted within the company to replace them. For this, we need to determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program. Then we need to deliver advice based on our analysis so that Bobby's boss can handle the “silver tsunami” as many current employees reach retirement age.

## Results

The results of the queries are described in the following sections.

### Deliverable 1: The Number of Retiring Employees by Title 

In order to check the scope of the "silver tsunami," we examined the number of current employees who are retirement age. 

1. First, we created a table where we joined information from the `employees` table and the `titles` table. This table was filtered for birth dates between 1952 and 1955. However, as illustrated in the image below, there were duplicates in the `retirement_titles.csv` table because employees could have been promoted and changed their title.

![There are duplicates in the retirement_titles table](https://github.com/saramcel/Pewlett-Hackard-Analysis/blob/414bd42fd70fdc5b8d81e65347a83b812a2b8fc2/Resources/table1.png)

2. Next, we created a table containing only the current title of the people in the previous table. We did this using `DISTINCT ON` for the employee number, and then filtering for `to_date = '9999-01-01'` which is a nonsense date that indicates that there is no end date for employment. This table is called `unique_titles.csv`.

3. Lastly, we wanted to figure out where the "silver tsunami" will hit hardest. We counted the retiring employees grouped by their title and found that there will be a huge number of Senior Engineer and Senior Staff positions to be filled. This is saved in the `retiring_titles.csv` table.

![There are many senior positions that will be vacated.](https://github.com/saramcel/Pewlett-Hackard-Analysis/blob/414bd42fd70fdc5b8d81e65347a83b812a2b8fc2/Resources/table2.png)

### Deliverable 2: The Employees Eligible for the Mentorship Program

Does Pewlett-Hackard already have the capacity to handle the "silver tsunami?" We are going to find out. There is a mentorship program that can help employees fill the senior positions. 

1. We ran a query to check who is eligible for the mentorship program. It turns out, 1,549 employees are eligible (there is a heading on the file pictured). The eligibility criteria are that the employee must currently be working at Pewlett-Hackard and they must have been born some time in the year 1965. 
   - We had to join three tables to gain this information: `employees`, `dept_emp`, and `titles`. 

![There are not enough people in the company who can be mentored to fill the positions. Remember there's a header, so it's only 1,549 employees.](https://github.com/saramcel/Pewlett-Hackard-Analysis/blob/70bb15070b970d07102074d45a7d7f725764a75c/Resources/table3.png)

## Summary

In conclusion, we can answer the following questions: 

**Q1.** How many roles will need to be filled as the "silver tsunami" begins to make an impact?
   
   **A1.** There will be 72,458 positions potentially affected by retirement. 
   
**Q2.** Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
   
   **A2.** Unfortunately, there are not enough mentors, because there are only 1,549 employees eligible for the mentorship program. 

Here are two suggested queries and tables that might provide more insight. 

**Query Suggestion 1:** 

We can set a wider range of birth years (e.g. 1960-1965) for the eligibility criteria for the mentorship program. Adjust the code in the Deliverable 2 coding block where the birth date was filtered with this code:

```
WHERE (de.to_date = '9999-01-01')
	AND (e.birth_date BETWEEN '1960-01-01' AND '1965-12-31')
```

This affects 93,756 rows of data. That means that adjusting the birth date criteria would allow more than enough mentors to be eligible. We know not every eligible employee will choose to mentor, and we know not every mentee will be hired to a senior position, so this gives us a little wiggle room.

**Query Suggestion 2:** 

We can add a filter to the retiring employees data. The modules had an additional filter on hire date, which we could apply here (please see below). 

```
WHERE (e.birth_date BETWEEN '1952-01-01' AND '1955-12-31')
	AND (e.hire_date BETWEEN '1985-01-01' AND '1988-12-31')
```

This results in 65,427 rows in the `retirement_titles` table, and 33,118 rows in the `unique_titles` table. Compared to the numbers in the challenfe, we have approximately half as many employees that are truly able to retire when we set this criteria in place. The distribution of the `retiring_titles` table is somewhat similar, but there are far fewer people we need to anticipate replacing (please see below). 

![There are fewer positions that will be vacated when we apply a hire_date filter.](https://github.com/saramcel/Pewlett-Hackard-Analysis/blob/39eaa5d3eaf47710ffdf5cb0a112b662cac3d940/Resources/table4.png)
