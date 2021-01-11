---
title: "Use Cases"
date: 2020-10-12T08:47:11+01:00
draft: false
---

#### Common Use Cases for window functions in analytics

* Cumulated Sum/Counts
* Group comparisons
* Ranking
* order or time related comparisons
```
SELECT hire_date, last_name, salary,
       LAG(salary, 1, 0) OVER (ORDER BY hire_date) AS prev_sal
FROM employees
WHERE job_id = 'PU_CLERK'
ORDER BY hire_date;
   
HIRE_DATE LAST_NAME                     SALARY   PREV_SAL
--------- ------------------------- ---------- ----------
18-MAY-03 Khoo                            3100          0
24-JUL-05 Tobias                          2800       3100
24-DEC-05 Baida                           2900       2800
15-NOV-06 Himuro                          2600       2900
10-AUG-07 Colmenares                      2500       2600
```
* missing value substituiton
* preceding and following
* top-n results

list examples here as sql code


* database support
table here with snowflake / bigquery / redshift

#### How they work
To understand how Analytical Functions are used in SQL statements, you really have to look at the four different parts of an Analytical ‘clause’:

the analytical function, for example AVG, LEAD, PERCENTILE_RANK
the partitioning clause, for example PARTITION BY job or PARTITION BY dept, job
the order by clause, for example order by job nulls last
the windowing clause, for example RANGE UNBOUNDED PRECEDING or ROWS UNBOUNDED FOLLOWING


#### Lateral (Table functions)
It is the "for-loop" of SQL.

Our example returns the count of occurences in table b which is associated with table a by ID given a specific start and end date.

What makes LATERAL special is that you can access columns in both directions, allowing to solve many problems which are dynamic in nature.


#### Common use-cases for lateral
* slicing dynamic windows of rows by column criterias (like start- and end_date)


```
SELECT ID, start_date, end_date, inner_query.occurences
FROM Table_A as a,
LATERAL 
(
    select count(id) as occurences
    from table_b as b
    where a.ID = b.ID
      and a.start_date >= b.date
      and a.end_date <= b.date
) as inner_query
```


#### Flatten
#### RLIKE
#### JSON
#### Event analysis
#### Geospatial functions
#### Aggregate Functions
#### Generator
#### sampling
#### HAVING, QUALIFY
#### Ranking
#### LAG/LEAD
#### Statistics library
#### Pattern matching
#### Advanced aggregations
#### Linear regression