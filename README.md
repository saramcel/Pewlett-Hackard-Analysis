# Pewlett-Hackard-Analysis

## Overview

### Purpose
We are preparing Bobby's boss at Pewelett-Hackard a dossier of employees who are retiring and those who might be promoted within the company to replace them. For this, we need to determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program. Then we need to deliver advice based on our analysis so that Bobby's boss can handle the “silver tsunami” as many current employees reach retirement age.

## Results

The results of the queries are described in the following sections.

### Deliverable 1: The Number of Retiring Employees by Title 

In order to check the scope of the "silver tsunami," we examined the number of current employees who are retirement age. 

1. First, we created a table where we joined information from the `employees` table and the `titles` table. This table was filtered for birth dates between 1952 and 1955. However, as illustrated in the image below, there were duplicates in the `retirement_titles.csv` table because employees could have been promoted and changed their title.

![There are duplicates in the retirement_titles table](table1.png)

2. Next, we created a table containing only the current title of the people in the previous table. We did this using `DISTINCT ON` for the employee number, and then filtering for `to_date = '9999-01-01'` which is a nonsense date that indicates that there is no end date for employment. This table is called `unique_titles.csv`.

3. Lastly, we wanted to figure out where the "silver tsunami" will hit hardest. We counted the retiring employees grouped by their title and found that there will be a huge number of Senior Engineer and Senior Staff positions to be filled. This is saved in the `retiring_titles.csv` table.

![There are many senior positions that will be vacated.](table2.png)

### Deliverable 2: The Employees Eligible for the Mentorship Program

## Summary


Results: Provide a bulleted list with four major points from the two analysis deliverables. Use images as support where needed.
Summary: Provide high-level responses to the following questions, then provide two additional queries or tables that may provide more insight into the upcoming "silver tsunami."
How many roles will need to be filled as the "silver tsunami" begins to make an impact?
Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
Deliverable 3 Requirements
Structure, Organization, and Formatting (6 points)
The written analysis has the following structure, organization, and formatting:

There is a title, and there are multiple sections. (2 pt)
Each section has a heading and subheading. (2 pt)
Links to images are working and displayed correctly. (2 pt)
Analysis (14 points)
The written analysis has the following:

Overview of the analysis:

The purpose of the new analysis is well defined. (3 pt)
Results:

There is a bulleted list with four major points from the two analysis deliverables. (6 pt)
Summary:

The summary addresses the two questions and contains two additional queries or tables that may provide more insight. (5 pt)****
