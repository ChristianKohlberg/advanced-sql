---
title: "Functions"
date: 2020-10-12T08:47:11+01:00
draft: false
---

This page gives a quick introduction into the different types of functions applicable to SQL queries. They can be combined arbitrarily and are flexible in nature. While you may find some of them **complicated** to start with, they have been given extensive thought when implementing.

#### Scalar functions
Scalar operations take a ***single*** value as input and return a single value as output. Most likely the technical term is more confusing than helping, just have a looka at our example below - the comparison operator **"> 1000"** is a scalar function which takes as input a dynamic value from the salary column and and *returns* either true or false depending on whether the salary was below or above 1000. It then filters out any rows which do not met the requirement of having a salary above 1000.

**Example:**
```
SELECT employee
FROM my_table
WHERE salary > 1000 
```

#### Aggregate functions
Aggregate functions take ***multiple*** values as input and return a **single value**. You always operate on the entire dataset but returning only aggregated results.

**Example 2:**
```
SELECT 
    max(salary) as highest_salary
  , sum(salary) as total_payroll
FROM my_table
```

**Example 2:**
```
SELECT 
  , sum(salary) as total_payroll_by_manager_id
FROM my_table
GROUP BY manager_id
```

#### Window functions
Window functions help to derive calculations over windows of rows. It is a subset of aggregate functions and therefore can operate on a subset of rows. It is similar like aggregate functions but on steroids. It takes some time to get used to it.

Our example returns the max salary in each window as MGR_MAX, written in a single query which is easy to read and write. 

It is most likely the most underused feature in SQL for analytical queries, while indeed tailored and developed to help analysts writing better and conciste SQL queries. It helps whenever you want to answer a question on subsets of your dataset like e.g. for each manager within your organization.

**Example 1:**
```
SELECT manager_id, last_name, salary,
  MAX(salary) OVER (PARTITION BY manager_id) AS mgr_max
FROM employees
ORDER BY manager_id, last_name, salary;

MANAGER_ID     LAST_NAME         SALARY    MGR_MAX
----------     ---------      ----------  ----------
  100           Zlotkey         10500       17000
  101           Baer            10000       12000
  101           Whalen           4400       12000
  102           Hunold           9000        9000
  103           Austin           4800        6000
```

**Example 2:**
```
WIP
```

#### Table functions
Table functions return results in tabular format. Table expresssions help to alter the structure of a table or to include more than a single table/relation into a single query.
**Table functions** are part of the basics we got teached at school (performing JOINs), but newly introduced functions like LATERAL and FLATTTEN make them really shine in our analytical queries. 

**Example:**
```
SELECT 
    ID, start_date, end_date
  , inner_query.occurences as occurences
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

The second approach follows use cases you encounter along your journey. You can solve nearly any problem by just altering and combining many examples into one bigger picture. Therefore solving one part of the analytical question aids in the process of finding a good solution approach.


References:
* [docs.snowflake.com](https://docs.snowflake.com/en/sql-reference/functions-analytic.html)  
* [informatik-aktuell.de](https://www.informatik-aktuell.de/betrieb/datenbanken/sql-performance-tuning-mit-analytic-functions-ein-projektbericht.html)

