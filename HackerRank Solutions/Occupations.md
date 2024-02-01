# Problem

Pivot the Occupation column in **OCCUPATIONS** so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively.

**Note:** Print **NULL** when there are no more names corresponding to an occupation.

## Input Format

The **OCCUPATIONS** table is described as follows:

![1443816414-2a465532e7-1](https://github.com/corneliuscornwallis3/SQL/assets/158492493/18abd1ac-e9a6-4a70-9c6a-0fb2d7cdfc21)

Occupation will only contain one of the following values: **Doctor**, **Professor**, **Singer** or **Actor**.

## Sample Input

![1443817648-1b2b8add45-2](https://github.com/corneliuscornwallis3/SQL/assets/158492493/f6c9205d-02bb-467b-a264-9693218c6b44)

## Sample Output
```
Jenny    Ashley     Meera  Jane
Samantha Christeen  Priya  Julia
NULL     Ketty      NULL   Maria
```

# Solution

```
create view pvt as (
    select
        case when occupation = 'Doctor' then name end as 'Doctor',
        case when occupation = 'Professor' then name end as 'Professor',
        case when occupation = 'Singer' then name end as 'Singer',
        case when occupation = 'Actor' then name end as "Actor",
    ROW_NUMBER() OVER (partition by occupation order by name) as row_num
    from occupations
);
SELECT MAX(Doctor),MAX(Professor),MAX(Singer),MAX(Actor) FROM pvt
group by row_num
```
