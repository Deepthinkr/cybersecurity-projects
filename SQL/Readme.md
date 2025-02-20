SQL Filters for Security Investigation and Employee Updates
Project Overview
This repository contains a portfolio project demonstrating the use of SQL queries with filters (WHERE, LIKE, AND, OR, NOT) to investigate security incidents and manage employee machine updates. The project uses two tables, log_in_attempts and employees, from an organization’s database. The tasks include analyzing login attempts for suspicious activity and identifying employees across departments and offices for security updates.
Files
Apply_filters_to_SQL_queries.md: The main document with detailed explanations, SQL queries, and project description/summary. (You can rename your completed template to this or keep it as a .docx file if preferred.)
README.md: This file.
Prerequisites
A SQL environment (e.g., MariaDB, MySQL) to run the queries.
Access to the log_in_attempts and employees tables as described in the table formats below.
Table Formats
log_in_attempts
Column
Description
event_id
Unique ID for each login event
username
Employee’s username
login_date
Date of the login attempt (YYYY-MM-DD)
login_time
Time of the login attempt (HH:MM:SS)
country
Country where the attempt occurred
ip_address
IP address of the employee’s machine
success
0 (FALSE) for failed, 1 (TRUE) for success
employees
Column
Description
employee_id
Unique ID for each employee
device_id
ID of the employee’s device
username
Employee’s username
department
Employee’s department
office
Employee’s office location (e.g., East-170)
SQL Queries
Below are the SQL queries developed for this project. Each addresses a specific task outlined in the scenario.
1. Retrieve After Hours Failed Login Attempts
Purpose: Identify failed login attempts after 18:00.
sql
SELECT event_id, username, login_date, login_time, success
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;
2. Retrieve Login Attempts on Specific Dates
Purpose: Review all login attempts on 2022-05-08 and 2022-05-09.
sql
SELECT event_id, username, login_date, login_time, success
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
3. Retrieve Login Attempts Outside of Mexico
Purpose: Exclude login attempts from Mexico (MEX or MEXICO).
sql
SELECT event_id, username, login_date, login_time, country, success
FROM log_in_attempts
WHERE country NOT LIKE '%MEX%' AND country NOT LIKE '%MEXICO%';
4. Retrieve Employees in Marketing
Purpose: Find Marketing employees in the East building.
sql
SELECT employee_id, device_id, username, department, office
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
5. Retrieve Employees in Finance or Sales
Purpose: Identify employees in Sales or Finance departments.
sql
SELECT employee_id, device_id, username, department, office
FROM employees
WHERE department = 'Sales' OR department = 'Finance';
6. Retrieve All Employees Not in IT
Purpose: Exclude Information Technology employees.
sql
SELECT employee_id, device_id, username, department, office
FROM employees
WHERE department NOT LIKE '%Information Technology%';
How to Use
Set Up the Database: Ensure the log_in_attempts and employees tables are created and populated in your SQL environment.
Run Queries: Copy and paste each query into your SQL client (e.g., MariaDB shell) to execute them.
Review Results: Analyze the output for security investigations or employee updates.
Screenshots: If desired, take screenshots of the queries running in your environment and add them to the Apply_filters_to_SQL_queries.md file.
Project Goals
Investigate potential security incidents by filtering login attempts by time, date, and location.
Support security updates by identifying employees across specific departments and offices.
Demonstrate proficiency in SQL filtering techniques (LIKE, AND, OR, NOT).
Summary
This project successfully applies SQL filters to address security and administrative needs. It retrieves data such as after-hours failed logins, login attempts on specific dates, and non-Mexico activity, while also identifying employees for targeted updates in Marketing, Sales, Finance, and non-IT departments. The use of pattern matching with LIKE and logical operators ensures precise and flexible data retrieval.
License
This project is unlicensed and intended for educational/portfolio purposes. Feel free to adapt it for your needs!

