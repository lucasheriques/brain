**TLDR: Indexing is crucial for high-performing applications. Indexes maintain a copy of part of your data in a separate data structure from your primary data structure. It's essential to create as many indexes as you need, but not too many, as this can impact performance. Access patterns should drive the creation of indexes, and application developers are usually best positioned to design them. In future content, we'll cover how indexes work, how to create them, and what makes a good or bad index.**

# [Indexing: the building blocks of database performance](https://planetscale.com/courses/mysql-for-developers/indexes/introduction-to-indexes?autoplay=1#indexing-the-building-blocks-of-database-performance)

At this point in the course, you're very familiar with schema design! Setting up your database schema is all about establishing the foundation of your database. But once that is done, the next step is to focus on indexing. Indexing is the best way to ensure that your queries perform well, which is essential for a high-performing application. In fact, indexes are ten times more important than schema design for performance! Maybe a hundred times more important.

In this video, we're going to give you a brief overview of indexing, characteristics of indexes, and a couple of rules for creating indexes.

## [Characteristics of indexes](https://planetscale.com/courses/mysql-for-developers/indexes/introduction-to-indexes?autoplay=1#characteristics-of-indexes)

Indexes are an entirely separate data structure that maintain a copy of part of your data. When you create an index, it creates a second data structure, which is different from your primary data structure (the table). It's crucial to understand that each index maintains a copy of part of your data, which means that if you have multiple indexes, there will be multiple copies of different parts of your data.

Moreover, indexes have a pointer back to the row. It's necessary for an index to know how to get back to the table because it maintains a copy of part of your data.

## [Rules for creating indexes](https://planetscale.com/courses/mysql-for-developers/indexes/introduction-to-indexes?autoplay=1#rules-for-creating-indexes)

As far as the rules for creating indexes are concerned, you should aim to create as many indexes as you need. Indexes are the best tool for creating a performant query, which usually translates into a performant application. However, you should also create as few as you can get away with because creating too many indexes can impact the performance.

It's essential to strike a balance between how many indexes you need and how few you can get away with. Establishing this balance depends on the size of your database, frequency of updates, and other factors that might influence the performance of your application. With that in mind, it's crucial to look at access patterns when deciding which indexes to create.

## [Creating optimal indexes](https://planetscale.com/courses/mysql-for-developers/indexes/introduction-to-indexes?autoplay=1#creating-optimal-indexes)

Unlike schema design, you cannot look at your data and decide what indexes to put on your table. Instead, you have to examine your queries to determine which indexes will perform the best. In other words, indexing should be driven by the access patterns of your application.

If you're an application developer who's writing the access patterns for your application, you're the best candidate to design indexes. You have insight into what the access patterns are and can create indexes accordingly.

## [Wrapping up](https://planetscale.com/courses/mysql-for-developers/indexes/introduction-to-indexes?autoplay=1#wrapping-up)

Indexes are essential for database performance, and once you've established your schema, indexing is the next step. Understanding the characteristics and rules for creating indexes is key to building a high-performing database. Keep in mind that indexing should be driven by access patterns, and application developers are usually in the best position to design indexes.

Stay tuned for more in-depth videos on indexing, where we'll cover how indexes work under the hood, how to create them, what makes a good index, and what makes a bad index.