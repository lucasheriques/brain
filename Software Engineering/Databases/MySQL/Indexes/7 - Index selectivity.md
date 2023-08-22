**TLDR: This article discusses two key concepts in MySQL indexing: cardinality and selectivity. Cardinality refers to the number of distinct values in an index column, while selectivity measures how unique the values in a column are. The higher the selectivity of an index, the better it is for optimizing query performance. Understanding these concepts can help make informed decisions when optimizing database performance, such as determining whether or not to put an index on a column based on its selective value. Additionally, checking the selectivity of an index can help troubleshoot issues where an index isn't being used. By using the right index on specific columns, we can optimize query performance and improve the speed of our databases.**

# [Understanding index cardinality and selectivity in MySQL](https://planetscale.com/courses/mysql-for-developers/indexes/index-selectivity?autoplay=1#understanding-index-cardinality-and-selectivity-in-mysql)

Indexing is a crucial aspect of MySQL database optimization. It involves adding indexes to important columns to speed up query performance. The process of selecting the best index for specific database columns can be a bit tricky. In this article, we'll dive deep into two essential concepts in MySQL indexing: cardinality and selectivity.

## [Defining cardinality and selectivity](https://planetscale.com/courses/mysql-for-developers/indexes/index-selectivity?autoplay=1#defining-cardinality-and-selectivity)

Cardinality refers to the number of distinct values in a particular column that an index covers. When you use the `SHOW INDEXES` command in MySQL, the `cardinality` column in the output shows you the approximate total number of unique values in a given index column.

Selectivity, on the other hand, refers to how unique the values in a column are. It is a measure of how selective an index can be in narrowing down results when queried. The higher the selectivity of an index, the better it is for optimizing query performance.

## [Practical implications of cardinality and selectivity](https://planetscale.com/courses/mysql-for-developers/indexes/index-selectivity?autoplay=1#practical-implications-of-cardinality-and-selectivity)

Knowing the concepts of cardinality and selectivity can help us make informed decisions when optimizing database performance. For instance, we can use the information on the selective value of a column to determine whether or not to put an index on it.

Suppose we have a table with a `type` column that has two possible values, `user` and `admin`, with most rows having the value `user`. In this case, putting an index on the `type` column may not be the best approach to find rows with `type = "user"` since most of the rows contain the same value. The index is not highly selective for `user`, but it is highly selective for `admin`!

Furthermore, if we're stuck and can't figure out why an index isn't being used, we can check the selectivity of the index in question. If the selectivity is low, it is most likely that MySQL decided to read the table, assuming the index would be slower than a full table scan.

## [Conclusion](https://planetscale.com/courses/mysql-for-developers/indexes/index-selectivity?autoplay=1#conclusion)

Cardinality and selectivity are two essential concepts in MySQL indexing that determine the optimal number of indexes to use on a particular column or table. By using the right index on specific columns, we can optimize query performance and improve the speed of our databases. Understanding the concepts of cardinality and selectivity can help us make better-informed decisions in our database optimization efforts.