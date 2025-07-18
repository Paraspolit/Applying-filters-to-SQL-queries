# Applying-filters-to-SQL-queries
Objective
In this lab, I apply additional filters to SQL queries to retrieve specific information from a database. I use standard SQL operators to filter data based on particular dates and times. Throughout this process, I execute SQL queries using the MariaDB shell. This is a Quciklabs-based project hosted on the Google Cloud platform. '

Skills Learned
Writing SQL queries to retrieve data from databases
Using a variety of operators to filter records based on specific conditions.
Using comparison and combining multiple conditions in SQL queries to narrow down search results.
Interacting with the MariaDB shell and reconnecting to the database if the session is unintentionally exited '
Tools and Environment Used
MariaDB
Linux
'

Scenario
In this project, you’re investigating a recent security incident.

You need to gather information about login attempts for certain dates and times. This will help in resolving a security incident.

You’ll first need to retrieve login events made after a certain date. Second, you’ll narrow the focus of the search to filter logins in a date range. Third, you’ll investigate logins that were made at certain times. Finally, filter login attempts based on their event IDs. '

My Procedure
I structured the procedure into four main tasks, as demonstrated below:

Task 1. Retrieve login attempts after a certain date
In this task, I am investigating a recent security incident. To do this, I need to gather information about login attempts made after a certain date. I carried out this task in two steps: '

To retrieve data for login attempts made after '2022-05-09', I completed the SQL query using the greater than operator:
```sql
SELECT *
FROM login_attempts
WHERE login_time > '2022-05-09';
```
<img width="1920" height="864" alt="Fig 1" src="https://github.com/user-attachments/assets/d46a262c-f617-4749-8165-ca6d21cf50bf" />



The number of login attempts made after '2022-05-09' is 125. '

Based on my initial query, I now needed to expand the date range to include login attempts made on or after '2022-05-09'. To do this, I completed the SQL query using the greater than or equal to operator:
```sql
SELECT *
FROM login_attempts
WHERE login_time >= '2022-05-09';
```
<img width="1920" height="872" alt="Fig 2" src="https://github.com/user-attachments/assets/e95945f9-1615-49b8-83b3-e9a3da8eebce" />


The number of login attempts made from 2022-05-09 onward is 165. '

Task 2. Retrieve login attempts after a certain date
In this task, I needed to narrow the focus of my search. I needed to exclude login attempts made after 2022-05-11. To achieve this, I used the BETWEEN and AND operators to return results between '2022-05-09' and '2022-05-11':
```sql
SELECT *
FROM login_attempts
WHERE login_time BETWEEN '2022-05-09' AND '2022-05-11';
```
<img width="1920" height="854" alt="image" src="https://github.com/user-attachments/assets/e55c7da5-07d4-433a-93ce-5a9d6738dd0e" />


123 login attempts were made between 2022-05-09 and 2022-05-11. '

Task 3. Investigate logins at certain times
In this task, I needed to investigate logins that occurred at specific times. To begin, I needed to filter the data in the login_attempts table by login time (login_time).

First, our organization's typical work hours begin at 07:00:00. I'd need to retrieve all login attempts made before 07:00:00 to understand more about the users who are logging in outside of these typical hours.

I wrote a SQL query to retrieve data for login attempts made before '07:00:00'
```sql
SELECT *
FROM login_attempts
WHERE TIME(login_time) < '07:00:00';
```
<img width="1920" height="882" alt="image" src="https://github.com/user-attachments/assets/104c1172-dbe4-4e2f-bbbc-c4ad2ed636e4" />


The username in the fifth record returned from this query is eraab.

The query in the previous step returned more results than required.
I'll modify the query to return logins between '06:00:00' and '07:00:00':
```sql
SELECT *
FROM login_attempts
WHERE TIME(login_time) BETWEEN '06:00:00' AND '07:00:00';
```
This query will select all rows from the login_attempts table where the time component of login_time falls between 06:00:00 and 07:00:00.

<img width="1892" height="626" alt="image" src="https://github.com/user-attachments/assets/dfe7bf0f-05f1-4d64-ad66-9541b9329483" />


The earliest login attempt was at 06:01:31

Task 4. Investigate logins by event ID
In the final task, I needed to investigate login attempts based on event ID numbers. For this query, I wanted to retrieve only the event_id, username, and login_date fields from the login_attempts table..

To filter for login attempts with event_id greater than or equal to 100, I wrote:
```sql
SELECT *
FROM login_attempts
WHERE event_id >= 100;
```
<img width="1920" height="886" alt="image" src="https://github.com/user-attachments/assets/4b9422cd-b20b-4549-b0e4-34fd62c76c62" />


The login date of the third result returned is 2022-05-09.

The query in the previous step returned more data than required. I then modified the query to filter only for login attempts with event_id between 100 and 150.
```sql
SELECT *
FROM login_attempts
WHERE event_id BETWEEN 100 AND 150;
```
This query selects all columns (*) from the login_attempts table where the event_id falls within the range of 100 to 150, inclusive. It filters specifically for login attempts with event_id values between 100 and 150.

<img width="1920" height="836" alt="image" src="https://github.com/user-attachments/assets/b492bb4b-4907-4220-8bbc-d5ad1f229bdf" />


The username of the seventh result is tmitchel.

Conclusion
The objective of this project was to apply SQL querying skills to investigate a recent security incident by filtering and analyzing login data stored in a MariaDB database. The tasks involved retrieving specific records based on date, time, and event ID criteria using various SQL operators and functions. By completing these tasks, I demonstrated my skills in data filtering, date and time handling, range queries, and an overall ability to handle real-world data-related workloads pertinent to a cybersecurity analyst's job.
