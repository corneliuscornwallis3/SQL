# Problem

You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.

![1443818507-5095ab9853-1](https://github.com/corneliuscornwallis3/SQL/assets/158492493/d2056073-7945-4fe6-8921-74311227cd0e)

Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:

   - Root: If node is root node.
   - Leaf: If node is leaf node.
   - Inner: If node is neither root nor leaf node.

## Sample Input

![1443818467-30644673f6-2](https://github.com/corneliuscornwallis3/SQL/assets/158492493/61a04bb3-922e-447e-975e-b38358a3c11e)

## Sample Output
```
1 Leaf
2 Inner
3 Leaf
5 Root
6 Leaf
8 Inner
9 Leaf
```
# Solution

```
select n,
    if(p is NULL, 'Root', if((select count(*) from bst where p = b.n)>0,'Inner','Leaf')) from bst as b order by n
```
