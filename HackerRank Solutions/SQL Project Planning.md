# Problem
You are given a table, Projects, containing three columns: Task_ID, Start_Date and End_Date. It is guaranteed that the difference between the End_Date and the Start_Date is equal to 1 day for each row in the table.

![1443819551-639948acc0-1](https://github.com/corneliuscornwallis3/SQL/assets/158492493/62dce983-f23b-40eb-8070-c32694a69116)

If the End_Date of the tasks are consecutive, then they are part of the same project. Samantha is interested in finding the total number of different projects completed.

Write a query to output the start and end dates of projects listed by the number of days it took to complete the project in ascending order. If there is more than one project that have the same number of completion days, then order by the start date of the project.

## Sample Input

![1443819440-1c40e943a1-2](https://github.com/corneliuscornwallis3/SQL/assets/158492493/0e92d64f-8f4c-4475-99c1-906f580fae4d)

## Sample Output
```
2015-10-28 2015-10-29
2015-10-30 2015-10-31
2015-10-13 2015-10-15
2015-10-01 2015-10-04
```

# Solution

```
select Start_Date, min(End_Date) from (
select Start_Date from projects where Start_Date not in (select End_Date from projects)
) as a,
(
select End_Date from projects where End_Date not in (select Start_Date from projects)
) as b
where Start_Date < End_Date
group by Start_Date
order by datediff(min(End_Date),Start_Date), Start_Date
```
