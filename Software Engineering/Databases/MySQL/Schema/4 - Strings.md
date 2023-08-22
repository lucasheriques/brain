**TLDR: When it comes to storing strings in MySQL, understanding the differences between fixed-length and variable-length columns is crucial. Additionally, character sets and collations play a vital role in determining what can be stored in a column and how different strings are compared or sorted. Keep in mind that for certain operations, MySQL allocates memory based on the maximum column size, so it's essential to choose the smallest possible data type for the data you are trying to store.**

There are a bunch of different ways to store a string in MySQL. Here's a list of ways that we can use. For now, we're only covering `CHAR` and `VARCHAR`.

1. `CHAR`: fixed character. If you have any data that is truly of fixed length, this is the one you should use. That would be things like 2 digits, prefixes, maybe MD5 hashes. Something that is always gonna be the same size.
2. `VARCHAR`: stands for "variable character". 
3. `BINARY`
4. `VARBINARY`
5. `BLOB`
6. `TEXT`
7. `ENUM`
8. `SET`

What matters when choosing `varchar` or `char`? Because of the underlying storage. If you declare that a column is fixed, that means that that column will always have that same number of characters.

If you have a `char(100)`, column, but use it to store your name, "Lucas", in my case, that means MySQL will fill that to its storing 100 characters. On a variable length column, you're only going to store the needed bytes.

## [Character sets and collations](https://planetscale.com/courses/mysql-for-developers/schema/strings?autoplay=1#character-sets-and-collations)

A character set defines what characters are allowed to go into a column. MySQL supports a wide range of character sets, which you can view from the `information_schema` database. `utf8` and `utf8mb4` are the character sets you will likely use, with the latter being the default in MySQL 8.

Collations, on the other hand, determine how two or more strings are compared or sorted. A collation is a group of rules that decide whether two strings are equivalent or not. The default collation for MySQL 8 is `utf8mb4_0900_ai_ci`, with the `ai` indicating that the collation is accent-insensitive, and `ci` meaning that it is case-insensitive.

```sql
CREATE TABLE strings (
  variable_length VARCHAR(100) CHARSET utf8mb4 COLLATE utf8mb4_general_ci
);
```

In the example above, we've created a `VARCHAR` column with a character set of `utf8mb4` and a collation of `utf8mb4_general_ci`.