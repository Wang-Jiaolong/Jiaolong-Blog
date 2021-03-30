---
layout: wiki
title: MySQL
categories: MySQL
description: some word here
keywords: MySQL
---





# SQL语句

## INSERT

```sql
INSERT INTO table_name ( field1, field2,...fieldN )
                       VALUES
                       ( value1, value2,...valueN );
```



## UPDATE

> 修改或更新 MySQL 中的数据

```sql
UPDATE table_name SET field1=new-value1, field2=new-value2
[WHERE Clause]
```



## ORDER BY

> 对读取的数据进行排序，我们就可以使用 MySQL 的 **ORDER BY** 子句来设定你想按哪个字段哪种方式来进行排序，再返回搜索结果。

```sql
SELECT field1, field2,...fieldN FROM table_name1, table_name2...
ORDER BY field1 [ASC [DESC][默认 ASC]], [field2...] [ASC [DESC][默认 ASC]]
```



## GROUP BY

> GROUP BY 语句根据一个或多个列对结果集进行分组。
>
> 在分组的列上我们可以使用 COUNT, SUM, AVG,等函数。

```SQL
SELECT column_name, function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name;
```



## 连接

> 使用 MySQL 的 JOIN 在两个或多个表中查询数据。

你可以在 SELECT, UPDATE 和 DELETE 语句中使用 Mysql 的 JOIN 来联合多表查询。

JOIN 按照功能大致分为如下三类：

- **INNER JOIN（内连接,或等值连接）**：获取两个表中字段匹配关系的记录。
- **LEFT JOIN（左连接）：**获取左表所有记录，即使右表没有对应匹配的记录。
- **RIGHT JOIN（右连接）：** 与 LEFT JOIN 相反，用于获取右表所有记录，即使左表没有对应匹配的记录。



`INNER JOIN`：来连接以上两张表来读取runoob_tbl表中所有runoob_author字段在tcount_tbl表对应的runoob_count字段值：

`MySQL LEFT JOIN`：MySQL left join 与 join 有所不同。 MySQL LEFT JOIN 会读取左边数据表的全部数据，即便右边表无对应数据。

`MySQL RIGHT JOIN`：MySQL RIGHT JOIN 会读取右边数据表的全部数据，即便左边边表无对应数据。