---
layout: wikis
title: SQL
description: sql一般指结构化查询语言。结构化查询语言（Structured Query Language）简称SQL
header-img: "img/about-bg.jpg"
catalog: true
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



**MySQL 拼音排序**

如果字符集采用的是 gbk(汉字编码字符集)，直接在查询语句后边添加 ORDER BY：

```SQL
SELECT * 
FROM runoob_tbl
ORDER BY runoob_title;
```

如果字符集采用的是 utf8(万国码)，需要先对字段进行转码然后排序：

```SQL
SELECT * 
FROM runoob_tbl
ORDER BY CONVERT(runoob_title using gbk);
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



## UNION 操作符

> MySQL UNION 操作符用于连接两个以上的 SELECT 语句的结果组合到一个结果集合中。多个 SELECT 语句会删除重复的数据。

```sql
SELECT 列名称 FROM 表名称 UNION SELECT 列名称 FROM 表名称 ORDER BY 列名称；
SELECT 列名称 FROM 表名称 UNION ALL SELECT 列名称 FROM 表名称 ORDER BY 列名称；
```

- **DISTINCT:** 可选，删除结果集中重复的数据。默认情况下 UNION 操作符已经删除了重复数据，所以 DISTINCT 修饰符对结果没啥影响。
- **ALL:** 可选，返回所有结果集，包含重复数据。



## 常用操作

### **查询某一列不重复的记录**

```sql
SELECT * FROM dbo.Member WHERE ID  IN (SELECT MIN(ID) FROM dbo.Member GROUP BY Name)
```

