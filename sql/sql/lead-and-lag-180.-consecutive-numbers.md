---
description: 'https://leetcode.com/problems/consecutive-numbers/'
---

# Lead and Lag: 180. Consecutive Numbers

This is a great example to use Lead and Lag Function

```text
Table: Logs

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| num         | varchar |
+-------------+---------+

```

id is the primary key for this table.

Write an SQL query to find all numbers that appear at least three times consecutively.

Return the result table in any order.



```text

Logs table:
+----+-----+
| Id | Num |
+----+-----+
| 1  | 1   |
| 2  | 1   |
| 3  | 1   |
| 4  | 2   |
| 5  | 1   |
| 6  | 2   |
| 7  | 2   |
+----+-----+

Result table:
+-----------------+
| ConsecutiveNums |
+-----------------+
| 1               |
+-----------------+
1 is the only number that appears consecutively for at least three times.
```

```sql
select  distinct Num as ConsecutiveNums 

from (
select Num, Lead(Num) over(order by Id) as Leads, 
            Lag(Num) over(order by Id) as Lags
from Logs) a

where Leads = num and Lags = num

```

Another way to solve this is of course using joins +1 and -1

```sql
select 
   distinct a.Num as ConsecutiveNums
from Logs a 
    join Logs b on
        a.Num = b.Num and
        b.Id -a.Id = 1
    join Logs c on 
        a.Num = c.Num and
        c.Id -a.Id = 2
        
        

```

