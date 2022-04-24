# Analysis of Pewlett Hackard's Employees Data

## Overview
### Analysis Purpose 
With the use of PostgresSQL, this analysis is carried out to help Bobby, who is the HR analyst at Pewlett Hackard Company, analyze their employee's database and generate a list of information on the retiring employees, in order to identify the number of positions that will need to be filled in the upcoming future, as well as, determine the list of retirees who are eligible for the retiree-to-newly-hired mentorship program. The analysis will help Bobby's manager be prepared for this forthcoming massive employment turnover. 

### Resources 
+ **Analysis Language**: SQL
+ **Database System**: PostgresSQL
+ **Interface**: pgAdmin
+ **Query for this analysis (Challenge query)**: in `Queries` folder 
	+ `Employee_Database_challenge.sql`
### Data
+ **All Employees Data**: in `Data/Module_Starter_Data` folder
+ **Analyzed Data Base (retiring employees)**: in `Data` folder
	+ `retirement_titles.csv` : list of retiring employees with their current and previous titles information
	+ `unique_titles.csv`: list of retiring employees with only their current title
	+ `retiring_titles.csv`: number of retiring employees per title
	+ `mentorship_eligibilty.csv`: list of retiring employees who are eligible for the mentorship program

## Analysis Results
> The retiring employees in this analysis are the ones who were born between 1952 and 1955.

1) In the `retirement_titles.csv`, which is the complete list of the retirees including all of their titles during the years with the company, some of the employees have held several positions over the years, as seen in the duplicate of their name with different titles. There will be an excessive number of retiring employees if we were to count them  from this table due to the name duplications (the total number of retiring employee count from this table is 133,776). The following image shows the duplication of the employees name. Some employees changed positions over times while some remain in the same title.

<img src= to-be-put-link width="50%" height="50%">

2) `unique_titles.csv` contains the list of the retiring employees with only their most recent title. The duplication of their name has been removed, and only the current position is stored in the table. Using another query, the correct total number of retiring employees is 72,458. 

<img src= to-be-put-link width="50%" height="50%">
<img src= to-be-put-link width="50%" height="50%">

3) `retiring_titles.csv` is the summary table of the retiring employees count per title, as show in the following image. From the table, largest number of retiring employees are on the senior level (Senior Engineer and Senior Staff) which are accounted for 70.17% of total.

<img src= to-be-put-link width="50%" height="50%">

4) `mentorship_eligibilty.csv` shows the list of employees who were born in the year 1965, which are considered as employees who are getting ready for the retirement and will be eligible for the mentorship program. (These eligible employees must be born between January 1, 1965 and December 31, 1965.)
There are the total of 1,549 retiring employees who are eligible for this mentorship program.

<img src= to-be-put-link width="50%" height="50%">



## Analysis Summary
1) Q:
  - how many roles need to be filled?
  - are there enough qualified mentors?

2) Two more queries/tables for more insight
