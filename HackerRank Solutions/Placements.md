# Problem

You are given three tables: Students, Friends and Packages. Students contains two columns: ID and Name. Friends contains two columns: ID and Friend_ID (ID of the ONLY best friend). Packages contains two columns: ID and Salary (offered salary in $ thousands per month).

![1443820186-2a9b4939a8-1](https://github.com/corneliuscornwallis3/SQL/assets/158492493/f4f76375-8992-43ef-a2fe-61361fc6e9e4)

Write a query to output the names of those students whose best friends got offered a higher salary than them. Names must be ordered by the salary amount offered to the best friends. It is guaranteed that no two students got same salary offer.

**Sample Input**

![1443820079-9bd1e231b1-2_1](https://github.com/corneliuscornwallis3/SQL/assets/158492493/fbee8261-4017-430d-871b-b8c870866c64)

![1443820100-adb691b2f5-2_2](https://github.com/corneliuscornwallis3/SQL/assets/158492493/cd791d2a-1666-41c3-96af-0f674c4aa04d)

**Sample Output**
```
Samantha
Julia
Scarlet
```

Explanation

See the following table:

![1443819966-c37c146d27-3](https://github.com/corneliuscornwallis3/SQL/assets/158492493/d616b7bf-a338-4984-b6a3-f0c5ac1e8308)

Now,

   - Samantha's best friend got offered a higher salary than her at 11.55
   - Julia's best friend got offered a higher salary than her at 12.12
   - Scarlet's best friend got offered a higher salary than her at 15.2
   - Ashley's best friend did NOT get offered a higher salary than her

The name output, when ordered by the salary offered to their friends, will be:

   - Samantha
   - Julia
   - Scarlet


# Solution

```
select s.name from (Students as s join friends as F using(ID)
                    join packages as p1 on s.id = p1.id
                    join packages as p2 on f.Friend_id = p2.id)
where p2.salary > p1.salary
order by p2.salary
```
