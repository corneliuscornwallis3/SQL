# Problem
Amber's conglomerate corporation just acquired some new companies. Each of the companies follows this hierarchy:

![1458531031-249df3ae87-ScreenShot2016-03-21at8 59 56AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/bb92a48d-fa9f-46d4-9956-a79463712863)

Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code.

**Note:**
- The tables may contain duplicate records.
- The company_code is string, so the sorting should not be numeric. For example, if the company_codes are C_1, C_2, and C_10, then the ascending company_codes will be C_1, C_10, and C_2.

## Input Format

The following tables contain company data:

   - Company: The company_code is the code of the company and founder is the founder of the company.

![1458531125-deb0a57ae1-ScreenShot2016-03-21at8 50 04AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/c975a0a2-8ca6-4047-b6b7-ed16829821e9)

   - Lead_Manager: The lead_manager_code is the code of the lead manager, and the company_code is the code of the working company.

![1458534960-2c6d764e3c-ScreenShot2016-03-21at8 50 12AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/4978823d-430a-4cfc-964a-1db1e290f40c)

   - Senior_Manager: The senior_manager_code is the code of the senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company.

![1458534973-6548194998-ScreenShot2016-03-21at8 50 21AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/03b820c0-c2ab-4ae9-bcee-5434c581334f)

   - Manager: The manager_code is the code of the manager, the senior_manager_code is the code of its senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company.

![1458534988-7fc0af46ce-ScreenShot2016-03-21at8 50 29AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/3b969a83-9b9c-49f0-9753-c0ae6a349f57)

   - Employee: The employee_code is the code of the employee, the manager_code is the code of its manager, the senior_manager_code is the code of its senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company.


# Solution

```
select distinct c.company_code, c.founder, count(distinct LM.lead_manager_code), count(distinct SM.senior_manager_code), count(distinct MM.manager_code), count(distinct EE.employee_code) from company as c
join Lead_Manager as LM
on c.company_code = LM.company_code
join Senior_Manager as SM
on LM.lead_manager_code = SM.lead_manager_code
join Manager as MM
on SM.senior_manager_code = MM.senior_manager_code
join Employee as EE
on MM.manager_code = EE.manager_code
group by c.company_code, c.founder order by c.company_code
```
