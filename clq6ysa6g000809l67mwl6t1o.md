---
title: "Join the SQL Party!"
datePublished: Fri Dec 15 2023 18:30:10 GMT+0000 (Coordinated Universal Time)
cuid: clq6ysa6g000809l67mwl6t1o
slug: join-the-sql-party
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700851005549/d423a96a-8cb6-4117-ba01-00644a7c58c5.png
tags: postgresql, mysql, databases, sql, sql-database-sqlquery-databasemanagement-datamanipulation-dataanalysis-structuredquerylanguage-sqltips-sqltricks-sqlsyntax-sqlbestpractices-sqlperformance-sqldatabase-sqlserver-sqltutorial-sqlqueries-sqldatabasemanagement-sqldatamanipulation-sqldataanalysis-sqllearning

---

### **Introduction**

Joins are a crucial concept in SQL that allow you to combine data from multiple tables. Understanding the different types of SQL joins and when to use each one is key for writing performant queries and effectively working with relational databases. In SQL, joins create a result set by combining data from multiple tables based on the join condition specified.

There are primarily four main types of joins supported in SQL - **inner join, left join, right join and full outer join.** An inner join is the most common join and includes records with matching values in both tables. A left join or right join includes all records from one table along with only matching records from the other table. A full outer join returns all matching records from both tables along with unmatched records as well.

Knowing how to use SQL joins allows extracting and analyzing combined data from multiple database tables. This serves various purposes like relating data between tables for easy understanding, aggregating related data in one result set for reporting and analytics, replacing repeated subqueries and more. Understanding types of joins also helps optimize query performance by only extracting required data.

In this post, we will explain the four standard joins in SQL along with examples and use cases. We’ll also include a comparison table outlining the differences and when each type of join is applicable.

### **Simpler explanation**

The easiest way to understand SQL joins is by relating them to Venn diagrams with overlapping circles. Each circle represents a table, overlapping regions represent matching records, and non-overlapping regions represent unmatched records.

An inner join only shows the overlapped region with matching records from both tables. A left join shows one whole table plus the overlap with the other table. Similarly, A right join includes the whole second table and overlaps. A full outer join displays all records from both tables by combining overlaps, lef table’s exclusive part and right table’s exclusive part.

So the type of join defines which table's data is wholly included, which areas are overlapped and which data is excluded in the result set based on matches.

### **Types of Joins**

* **Inner join**
    
    * Includes records with matching values in both tables
        
    * One of the most commonly used joins
        

```sql
SELECT * FROM Table_A INNER JOIN Table_B ON Table_A.key = Table_B.key;
```

* **Left join**
    
    * Includes all records from left table along with matching records from right table
        
    * Right table records without matches are excluded
        

```sql
SELECT * FROM Table_A LEFT JOIN Table_B ON Table_A.key = Table_B.key;
```

* **Right join**
    
    * Includes all records from right table along with matching records from left table
        
    * Left table records without matches are excluded
        

```sql
SELECT * FROM Table_A RIGHT JOIN Table_B ON Table_A.key = Table_B.key;
```

* **Full outer join**
    
    * Most comprehensive join with all matching and non-matching records
        

```sql
SELECT * FROM Table_A FULL OUTER JOIN Table_B ON Table_A.key = Table_B.key;
```

### **Comparison Table**

| Join Type | Includes Records From Left Table | Includes Records From Right Table | Includes Matches Only |
| --- | --- | --- | --- |
| Inner join | Yes | Yes | Yes |
| Left join | Yes | Only matches | No |
| Right join | Only matches | Yes | No |
| Full outer join | Yes | Yes | No |

### **Conclusion**

SQL joins enable combining relevant data from multiple tables in a database to extract comprehensive and insightful information. Understanding how to effectively use inner joins, left joins, right joins and full outer joins is an essential skill for any SQL developer or data analyst. Knowing the nuances of each join type in terms of included vs excluded records can help write optimized query statements. Referencing join examples and comparison tables serves as a helpful quick guide for deciding the appropriate join to use based on the business requirements.

### **References**

1. [https://www.w3schools.com/sql/sql\_join.asp](https://www.w3schools.com/sql/sql_join.asp)
    
2. [https://www.geeksforgeeks.org/sql-join-set-1-inner-left-right-and-full-joins/](https://www.geeksforgeeks.org/sql-join-set-1-inner-left-right-and-full-joins/)