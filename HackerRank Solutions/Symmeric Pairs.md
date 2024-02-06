# Problem

You are given a table, Functions, containing two columns: X and Y.

![1443818798-51909e977d-1](https://github.com/corneliuscornwallis3/SQL/assets/158492493/5d40c5fe-c002-4da0-9879-e5d23a0ff42d)

Two pairs (X1, Y1) and (X2, Y2) are said to be symmetric pairs if X1 = Y2 and X2 = Y1.

Write a query to output all such symmetric pairs in ascending order by the value of X. List the rows such that X1 ≤ Y1.

## Sample Input

![1443818693-b384c24e35-2](https://github.com/corneliuscornwallis3/SQL/assets/158492493/fdc2e9e7-f136-4902-954a-65096783b954)

## Sample Output
```
20 20
20 21
22 23
```

# Solution

```
SELECT f1.X, f1.Y FROM Functions AS f1 
WHERE f1.X = f1.Y AND
(SELECT COUNT(*) FROM Functions WHERE X = f1.X AND Y = f1.Y) > 1
UNION
SELECT f1.X, f1.Y from Functions AS f1
WHERE EXISTS(SELECT X, Y FROM Functions WHERE f1.X = Y AND f1.Y = X AND f1.X < X)
ORDER BY X;
```
