### [197\. Rising Temperature](https://leetcode.com/problems/rising-temperature/description/)

Difficulty: **Easy**



Given a `Weather` table, write a SQL query to find all dates' Ids with higher temperature compared to its previous (yesterday's) dates.

```
+---------+------------------+------------------+
| Id(INT) | RecordDate(DATE) | Temperature(INT) |
+---------+------------------+------------------+
|       1 |       2015-01-01 |               10 |
|       2 |       2015-01-02 |               25 |
|       3 |       2015-01-03 |               20 |
|       4 |       2015-01-04 |               30 |
+---------+------------------+------------------+
```

For example, return the following Ids for the above `Weather` table:

```
+----+
| Id |
+----+
|  2 |
|  4 |
+----+
```



#### Solution
```sql
# Write your MySQL query statement below
SELECT A.Id
FROM Weather AS A
WHERE A.Temperature > (SELECT B.Temperature FROM Weather AS B 
                        WHERE to_days(B.RecordDate) = to_days(A.RecordDate) - 1)
```