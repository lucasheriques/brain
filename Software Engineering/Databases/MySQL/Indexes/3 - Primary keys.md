**TLDR: The primary key is a unique identifier for each row in a MySQL table, and choosing the right one is important for performance. A primary key is required for many database operations and determines how data is physically ordered on disk. Choosing an auto-incrementing integer as a primary key can be more efficient than using a GUID or hash. Secondary keys are used to improve query performance and are any index that is not the primary key. Understanding the structure of B+ trees, how to create tables, and the differences between primary and secondary keys is essential for creating efficient and scalable MySQL databases.**

When it comes to creating tables in MySQL, one of the most important decisions you'll make is selecting the primary key. A primary key is a unique identifier for each row in the table, and it plays an important role in how your data is stored and accessed.

Let's dive into the practical side of creating a table, adding a primary key, and understanding how it relates to secondary keys. We'll also explore the structure of an index, how it's implemented as a B+ tree under the hood, and why choosing the right primary key is so important.

## [Creating a table and adding a primary key](https://planetscale.com/courses/mysql-for-developers/indexes/primary-keys?autoplay=1#creating-a-table-and-adding-a-primary-key)

Let's start by creating a users table and adding a primary key. There are a few different ways to declare a primary key, but we'll focus on the most common method. We'll call our primary key `ID` and give it the datatype `BIGINT`:

```sql
CREATE TABLE users (
  ID BIGINT PRIMARY KEY,
);
```

Keep in mind that while this is the simplest method, there are some things to be aware of. For example, MySQL will automatically make the primary key column not nullable, and it will create a unique index for the column. This means that you don't need to create a separate index for the primary key, and doing so could result in duplicated indexes.

To check the structure of your table, you can use the `SHOW CREATE TABLE` command. This will show you the column names, data types, and other information about the table including the primary key. You can also use the `SHOW INDEXES` command to see the indexes created by MySQL.

## [Understanding primary keys vs. secondary keys](https://planetscale.com/courses/mysql-for-developers/indexes/primary-keys?autoplay=1#understanding-primary-keys-vs-secondary-keys)

Before we dive deeper into primary keys, let's clarify the difference between primary keys and secondary keys. A secondary key is any index that is not the primary key. It's used to improve performance when searching for specific data in your table.

A primary key, on the other hand, is a unique identifier for each row in the table. It's required for many relational database operations. In MySQL, the primary key is used to determine the physical order of the data in the table. This means that choosing the right primary key is critical for optimizing performance.

## [Why choosing the right primary key matters](https://planetscale.com/courses/mysql-for-developers/indexes/primary-keys?autoplay=1#why-choosing-the-right-primary-key-matters)

The primary key determines how your data is stored on disk. In MySQL's InnoDB engine, the primary key is a "clustered index," which means that the data is physically ordered based on the values in the primary key column. This makes primary key lookups incredibly fast, but it also means that every time you insert a new row the tree structure has to be updated.

Choosing a good primary key is important because it can impact the performance of your queries. For example, using a GUID or hash as a primary key can be slow because it requires more storage space and can lead to slower insert performance as the tree has to be rebalanced. On the other hand, using an auto-incrementing integer as a primary key can be more efficient because it requires less storage space and new values always go at the end.

## [Conclusion](https://planetscale.com/courses/mysql-for-developers/indexes/primary-keys?autoplay=1#conclusion)

Understanding primary and secondary keys is essential for creating efficient and scalable MySQL databases. Choosing the right primary key is critical for optimizing query performance and ensuring that your data is stored correctly. By understanding B+ tree structure and using the right data types, you can create tables that are both easy to work with and highly performant.