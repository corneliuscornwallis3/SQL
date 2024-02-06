# Problem

Write a query identifying the type of each record in the **TRIANGLES** table using its three side lengths. Output one of the following statements for each record in the table:

- **Equilateral**: It's a triangle with 3 sides of equal length.
- **Isosceles**: It's a triangle with 2 sides of equal length.
- **Scalene**: It's a triangle with 3 sides of differing lengths.
- **Not A Triangle**: The given values of A, B, and C don't form a triangle.

## Input Format

The TRIANGLES table is described as follows:

![1443815629-ac2a843fb7-1](https://github.com/corneliuscornwallis3/SQL/assets/158492493/e73300d9-431b-41a1-944c-64c177ffa857)

Each row in the table denotes the lengths of each of a triangle's three sides.

## Sample Input

![1443815827-cbfc1ca12b-2](https://github.com/corneliuscornwallis3/SQL/assets/158492493/ab53bdf5-8986-4242-8638-92a656523c7e)

## Sample Output
```
Isosceles
Equilateral
Scalene
Not A Triangle
```

# Solution

```
select case
    when A + B <= C or B + C <= A  or A + C <= B then 'Not A Triangle'
    when A = B and B = C then 'Equilateral'
    when A = B or A = C or B = C then 'Isosceles'
    else 'Scalene'
end
from triangles;
```
