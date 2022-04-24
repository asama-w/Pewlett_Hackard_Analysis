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
> The retiring employees in this analysis are the ones who were born between the year 1952 and year 1955.

1) In the `retirement_titles.csv`, which is the complete list of the retirees including all of their titles during the years with the company, some of the employees have held several positions over the years, as seen in the duplicate of their name with different titles. There will be an excessive number of retiring employees if we were to count them  from this table due to the name duplications (the total number of retiring employee count from this table is 133,776). The following image shows the duplication of the employees name. Some employees changed positions over times while some remain in the same title.

<img src= https://github.com/asama-w/Pewlett_Hackard_Analysis/blob/main/Additional_Images/retirement_titles_table.png width="70%" height="70%">
<img src= https://github.com/asama-w/Pewlett_Hackard_Analysis/blob/main/Additional_Images/retiree_count_w_query_dupl.png width="50%" height="50%">

2) `unique_titles.csv` contains the list of the retiring employees with only their most recent title. The duplication of their name has been removed, and only the current position is stored in the table. Using another query, the correct total number of retiring employees is 72,458. 

<img src= https://github.com/asama-w/Pewlett_Hackard_Analysis/blob/main/Additional_Images/unique_titles_table.png width="50%" height="50%">
<img src= https://github.com/asama-w/Pewlett_Hackard_Analysis/blob/main/Additional_Images/retiree_count_w_query_correct.png width="50%" height="50%">

3) `retiring_titles.csv` is the summary table of the retiring employees count per title, as show in the following image. From the table, largest number of retiring employees are on the senior level (Senior Engineer and Senior Staff) which are accounted for 70.17% of total.

<img src= https://github.com/asama-w/Pewlett_Hackard_Analysis/blob/main/Additional_Images/retirees_count_per_title.png width="25%" height="25%">


Adding the total percentage by title summary for the ease of analysis.

```sql
-- Calculate Total Percentage by Title
SELECT *, ROUND(100*(count/sum(count) over ()),3) AS "% of Total"
FROM retiring_titles;
```

The table is now shown as in the following image.

<img src= https://github.com/asama-w/Pewlett_Hackard_Analysis/blob/main/Additional_Images/retiring_titles_w_percentage.png width="30%" height="30%">

4) `mentorship_eligibilty.csv` shows the list of employees who were born in the year 1965, which are considered as employees who are getting ready for the retirement and will be eligible for the mentorship program. (These eligible employees must be born between January 1, 1965 and December 31, 1965.)
There are the total of 1,549 retiring employees who are eligible for this mentorship program.

<img src= https://github.com/asama-w/Pewlett_Hackard_Analysis/blob/main/Additional_Images/membership_eligible_table.png width="70%" height="70%">


## Analysis Summary
Additional queries which can be used to for more insight of the data
1) Determine the number of membership-eligible employees per title are shown as follow.
```sql
-- Count number of eligible retiring employees for mentorship
SELECT title, count(emp_no) as total_eligible_emp
FROM membership_eligibility
GROUP BY title
ORDER BY total_eligible_emp DESC;
```
Total nunmber of membership-eligible employees is 1,549.

<img src= https://github.com/asama-w/Pewlett_Hackard_Analysis/blob/main/Additional_Images/membership_eligible_count_by_title.png width="30%" height="30%">

2) Determine total number of employee in the company (no hired date boundary) for the comparison with the number of retiring employees

```sql
-- Determine number of all current employees
SELECT count(emp_no) as all_emp_count
FROM all_emp_info;
```

<img src= https://github.com/asama-w/Pewlett_Hackard_Analysis/blob/main/Additional_Images/all_emp_count.png width="20%" height="20%">

Note:
Total number of the current employees (all ages) is 240,124.
While there are 72,458 employees who will be retired in the near future, which is approximately 30.2% of the total number of all employees. Thus, there will be 72,458 vacant roles which need to be filled.

However, the total number of those who are eligible for the mentorshop program is only 1,549, which is only 2.1% of the number of future newly-hired.
No manager eligible for the mentorship
