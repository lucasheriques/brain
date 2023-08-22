**TLDR: The article discusses how to use indexes effectively to optimize database queries in MySQL. It suggests that queries should drive indexes, meaning you should analyze the access patterns of your application before deciding where to put indexes. Not all queries require indexes, and adding too many indexes can harm the database's performance.**

**The article provides general guidelines on when and how to use indexes, such as considering the entire query when deciding which columns to index and not creating an index on every column. It also discusses how to add an index in MySQL and provides examples of how indexes can optimize specific queries involving equality, ranges, sorting, and grouping.**

**The article concludes by emphasizing that indexing is an art that requires skill and time to learn. By following best practices and analyzing queries and access patterns, you can find the right balance of indexes to optimize your database queries without compromising performance.**


# [A guide to using indexes in MySQL](https://planetscale.com/courses/mysql-for-developers/indexes/where-to-add-indexes?autoplay=1#a-guide-to-using-indexes-in-mysql)

In the previous section, we learned about primary keys and secondary keys, as well as B-trees and how they relate to each other. However, we still don't know how to _apply_ this knowledge to optimize our database performance. In this video, we will dive into how to use indexes effectively to improve query performance.

## [Start with your queries](https://planetscale.com/courses/mysql-for-developers/indexes/where-to-add-indexes?autoplay=1#start-with-your-queries)

We've said before that your queries should drive your indexes. What does this mean? It means that you should start by analyzing the access patterns of your application before deciding where to put indexes.

Before adding an index, ask yourself, which queries are you running frequently and which tables are they accessing? By analyzing the access patterns of your queries, you can better determine which indexes will be most useful. Keep in mind that not all queries require indexes, and adding too many indexes can actually harm your database's performance.

## [When to use indexes](https://planetscale.com/courses/mysql-for-developers/indexes/where-to-add-indexes?autoplay=1#when-to-use-indexes)

Here are some general rules of thumb to consider when deciding whether or not to use an index:

-   Do not assume that anything that shows up in the where clause of a query should have an index. Consider all queries being run and their respective access patterns.
-   Do not create an index on every column. This will slow down inserts by functionally duplicating your table. It also won't help reads as much as you'd hope.
-   Do consider the entire query when deciding which columns to index. This includes sorting, grouping, and joining.
-   Do not worry about trying to create the perfect index for every query. It may not always be possible, and sometimes you will have to rework the queries to take advantage of existing indexes.

## [Adding an index in MySQL](https://planetscale.com/courses/mysql-for-developers/indexes/where-to-add-indexes?autoplay=1#adding-an-index-in-mysql)

Here's an example of how to add an index to a table in MySQL:

```sql
alter table people add index birthday_index (birthday);
```

This creates an index named `birthday_index` on the `birthday` column of the `people` table.

## [Using indexes for specific queries](https://planetscale.com/courses/mysql-for-developers/indexes/where-to-add-indexes?autoplay=1#using-indexes-for-specific-queries)

Let's take a closer look at how indexes can optimize specific queries. We will be using the `people` table we used in the previous section, which includes an `id`, `first_name`, `last_name`, `state`, `email`, and `birthday` column.

### [Equality](https://planetscale.com/courses/mysql-for-developers/indexes/where-to-add-indexes?autoplay=1#equality)

The most basic use of an index is for direct access, where the query searches for a specific value in a particular column. Here's an example:

```sql
select * from people where birthday = '1989-02-14';
```

Here, we're finding all people whose birthday is February 14th, 1989. Since there is an index on the `birthday` column, MySQL can use this index to find the rows that match the query, resulting in a low execution time.

### [Ranges](https://planetscale.com/courses/mysql-for-developers/indexes/where-to-add-indexes?autoplay=1#ranges)

Indexes can also be used for unbounded and bounded ranges, where a query requests all rows that fall within a certain range. In unbounded ranges, there is either no upper or lower limit on the range. Here's an example:

```sql
select * from people where birthday >= '2006-01-01';
```

This query finds all people born on or after January 1st, 2006. Since there is an index on the `birthday` column, MySQL can use this index to find the rows that match the query.

In bounded ranges, there are upper and lower limits on the range. Here's an example:

```sql
select * from people where birthday between '2006-01-01' and '2006-12-31';
```

This query finds all people born in the year 2006. We're using the `between` keyword to set the upper and lower bounds on the range. Once again, since there is an index on the `birthday` column, MySQL can use this index to find the rows that match the query.

### [Sorting](https://planetscale.com/courses/mysql-for-developers/indexes/where-to-add-indexes?autoplay=1#sorting)

Indexes can also be used to sort rows instead of having MySQL do a full table scan. Here's an example of a sorted query:

```sql
select * from people order by birthday limit 10;
```

This query will return the first 10 rows of the `people` table sorted by the `birthday` column. Since there is an index on the `birthday` column, MySQL can use this index for sorting instead of doing a full table scan.

### [Grouping](https://planetscale.com/courses/mysql-for-developers/indexes/where-to-add-indexes?autoplay=1#grouping)

Indexes can also be used to group rows together for an aggregate function. Here's an example:

```sql
select birthday, count(*) from people group by birthday;
```

This query groups all people by their birthdays and returns a count of all people born on the same day. Once again, since there is an index on the `birthday` column, MySQL can use this index to group rows together instead of doing a full table scan.

## [Conclusion](https://planetscale.com/courses/mysql-for-developers/indexes/where-to-add-indexes?autoplay=1#conclusion)

In this article, we've learned how to use indexes effectively to optimize our database queries. We started by discussing how queries should drive indexes, and provided guidelines on when and how to use indexes. We then explored how to add an index in MySQL, and provided examples of how indexes can optimize specific queries involving equality, ranges, sorting, and grouping.

Remember, indexing is an art that requires skill and time to learn. By following best practices and analyzing your queries and access patterns, you can find the right balance of indexes to optimize your database queries without compromising performance.