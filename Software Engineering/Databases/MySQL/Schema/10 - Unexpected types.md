**TLDR: MySQL has some unconventional data types, including booleans (represented as a `TINYINT`), zip codes (best stored as 5-character strings), and IP addresses (can be stored as integers or a binary column). By understanding these data types and their implications, you can store data in the most efficient way possible for querying and analysis. It's important to have a good handle on your data and make sure you're storing it in the most appropriate way.**

As a programmer, you're probably familiar with a variety of data types — strings, numbers, dates, and JSON, among others. But did you know that there are a few data types that are a little more unusual? In this video, we'll take a look at some of the more fun and wacky data types in MySQL.

## [MySQL Booleans](https://planetscale.com/courses/mysql-for-developers/schema/unexpected-types?autoplay=1#mysql-booleans)

Let's start with booleans. While booleans are a common data type in many languages, MySQL doesn't actually have a native boolean type. Instead, MySQL uses a `TINYINT` column to simulate a boolean value.

However, you can still use the keyword `BOOLEAN` in your table definition, which will be interpreted as a `TINYINT` column. The `BOOLEAN` keyword is just a shorthand way of creating a tiny int column, defaulting to null.

You can also create a boolean value using a zero-length character column that's nullable. However, this method is less recommended as it can make your data look confusing and difficult to understand. It is neat though!

## [Zip codes](https://planetscale.com/courses/mysql-for-developers/schema/unexpected-types?autoplay=1#zip-codes)

When it comes to USA zip codes, they are always 5 digits long. However, sometimes these codes may also include leading zeros. If you store these zip codes as integers, any leading zeros would be stripped, resulting in missing data.

As such, it's usually better to store zip codes as 5 character strings. However, if you need to store an extended zip code (which includes a dash and an additional 4 digits), you'll need to create a string column that's 10 characters long.

It's essential to understand data when it comes to zip codes, as there are exceptions to the rule. For example, there's a Saks Fifth Avenue in New York that has its own zip code: "10022-SHOE." Always make sure you have a good handle on your data before deciding how to store it.

## [IP addresses](https://planetscale.com/courses/mysql-for-developers/schema/unexpected-types?autoplay=1#ip-addresses)

Finally, let's take a look at IP addresses. While they usually appear as strings, you can also store them as integers for better organization and analysis.

MySQL has a built-in function `INET_ATON()` that converts an IPv4 address to an integer, and `INET_NTOA()` to convert an integer back to an IP address.

If you need to support both IPv4 and IPv6 addresses, you may need to use a binary column that's 16 bytes long.

# [Conclusion](https://planetscale.com/courses/mysql-for-developers/schema/unexpected-types?autoplay=1#conclusion)

While these data types might seem a little strange, they are illustrative of a point that by understanding the implications of data types and storing data in the most efficient way possible, you can set yourself up for success when it comes to querying and analyzing your data.

So take the time to explore your data, think about the most efficient way to store it, and have fun with these unusual data types. You never know how they might come in handy!