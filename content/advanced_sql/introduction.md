---
title: Introduction
draft: false
weight: 1
---


Welcome to our course about writing analytical queries in SQL. This course is part of a webinar to teach analytical problem solving with assistance of SQL.

> Modern SQL can do way more than you anticipate.

#### SQL in 2021+ (WIP)
The language is old but has just been recently seen a renaissance in usage when most other projects for data manipulation didnt provide a better experience for working with data. Namely spark, python, pandas, tableau, DAX and so much more.

It means that SQL will continue to dominate our industry for the next decade and as an analyst you will have to deal with it...

It is the only mature language to deal with Big Data (in a comfortable manner)


#### Requirements
This course expects **limited exposure** to SQL in the past - you may have written a few simple queries in the past or worked with something similar to SQL to retrieve data from a system. You dont need to understand all the details yet. **Our intent is to give you an overview of what is possible**. 

If you encounter an issue in the future and remember that a concept from this course could be of help - we personally think its a success and the true intent of this course is to get you started to incorporate SQL in your daily work.


#### Selectable
Below is the **Hello World** of analytical queries. If it looks unfamiliar to you - dont worry, focus on the problem solving instead of understanding the syntax of SQL. It is much easier to learn SQL by solving your own analytical questions anyway!

```
SELECT last_name, salary
FROM employees;
```

**Management:** This is not to teach about database management. We want you to become a better **analyst**. It means that we never alter the state of the database itself. This is important as successful database management is still **hard** to get right and many database administrators have serious concerns about the integrity of the system. If you plan to work on your database system, ask your database administrator about limited access to the database - most of the time it means getting a read-only access.


#### Databases
For this course we will use a cloud database called **snowflake**. It has a vibrant community and excellent analytical support. Most of the examples can be **copied** over to other databases like MySQL, Postgres, BigQuery or Redshift. Be aware that analytical support across databases is still immature in terms of consistency - something im sure of will diminish in the next few years.