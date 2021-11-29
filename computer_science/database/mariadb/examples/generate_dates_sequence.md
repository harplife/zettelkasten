---
aliases: [Generate a List of Dates]
tags: [mariadb, example, how-to]
status: complete
edited: 2021-11-29
---

# Generate a List of Dates
Works with MariaDB version 10.4.16

```SQL
SELECT DTSEQ.Date, YEAR(DTSEQ.Date) AS Year , WEEK(DTSEQ.Date) AS Week FROM (  
  SELECT curdate() - INTERVAL ( a.num + (10 * b.num) + (100 * c.num) + (1000 * d.num) ) DAY AS Date  
  FROM (  
    SELECT 0 AS num UNION ALL SELECT 1 UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4 UNION ALL SELECT 5 UNION ALL SELECT 6 UNION ALL SELECT 7 UNION ALL SELECT 8 UNION ALL SELECT 9  
  ) AS a  
  CROSS JOIN (SELECT 0 AS num UNION ALL SELECT 1 UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4 UNION ALL SELECT 5 UNION ALL SELECT 6 UNION ALL SELECT 7 UNION ALL SELECT 8 UNION ALL SELECT 9) AS b  
  CROSS JOIN (SELECT 0 AS num UNION ALL SELECT 1 UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4 UNION ALL SELECT 5 UNION ALL SELECT 6 UNION ALL SELECT 7 UNION ALL SELECT 8 UNION ALL SELECT 9) AS c  
  CROSS JOIN (SELECT 0 AS num UNION ALL SELECT 1 UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4 UNION ALL SELECT 5 UNION ALL SELECT 6 UNION ALL SELECT 7 UNION ALL SELECT 8 UNION ALL SELECT 9) AS d  
) AS DTSEQ  
WHERE DTSEQ.Date BETWEEN '2014-07-01' AND '2015-06-30'
;
```

How this query works:
1. Generate a sequence of numbers, 0 to 9,999. Adding more `CROSS JOIN ..` increases the sequence by x10 (e.g. 9,999 => 99,999).
2. Subtract current date `curdate()` with each number `- INTERVAL n DAY` (e.g. 2021/11/29 - INTERVAL 1 DAY = 2021/11/28).
3. Select rows between two dates.

It's not the prettiest of solutions, but I haven't yet found any other solution that works.
Apparently there is such a thing as `sequence`, so I need to research this further.

## Use Cases
Context: building a web page that shows a line graph with two lines, each line representing values within a date range, intervals by week (e.g. w1 : 3, 5, w2: 4, 6, ..).

Data A : values from 2014/07/01 to 2015/06/30
Data B : values from 2015/07/01 to 2016/06/30

Problem: `GROUP BY Week` does not take into account a week without any data. Meaning, a week without data will simply not exist (no `null` nor `0`). Since both data starts at 07/01, they should start on Week 26, but Data A starts on Week 27 because there are no values within Week 26. Because of this, the line graph initializes and starts from Week 27, thereby representing wrong values for Data B (in other words, Data B Week 26 value is on Week 27).

To make things worse, this needs to be solved without editing the frontend.

Solution: generate a list of dates (weeks), and join it with the data. Dates from both data should always match (unless of course, the date range is different, then it's all hell breaks loose).