### [175\. Combine Two Tables](https://leetcode.com/problems/combine-two-tables/description/)

Difficulty: **Easy**



Table: `Person`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |
+-------------+---------+
PersonId is the primary key column for this table.
```

Table: `Address`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |
+-------------+---------+
AddressId is the primary key column for this table.
```

Write a SQL query for a report that provides the following information for each person in the Person table, regardless if there is an address for each of those people:

```
FirstName, LastName, City, State
```



#### Solution
```sql
# Write your MySQL query statement below
SELECT P.FirstName, P.LastName, A.City, A.State
FROM Person AS P
LEFT JOIN Address AS A
ON P.PersonId = A.PersonId
```