**TLDR: `TEXT` and `BLOB` columns are useful data types in MySQL for storing large amounts of text and binary data. They have different variations available depending on how much data you need to store. While they have benefits in terms of storage, it's important to follow best practices to avoid potential issues with indexing, sorting and retrieval speed.**

5. `BLOB`: hold huges amount of characters data, but has no character set or collations.
	1. `TINYBLOB`, `BLOB`, `MEDIUMBLOB`, `LONGBLOB`
Some people also put files on the database, but that's not recomended. Much better to store that somewhere else, and leave a pointer on the database. It can be done, but not recommended.

6. `TEXT`: character column that hold huges amount of sets, but has a character set and collacion just like `CHAR` and `VARCHAR`.
	1. `TINYTEXT` (not really worth it, just use a `VARCHAR`), `TEXT`, `MEDIUM`, `LONG`


If you do end up using any of these columns, you need to be careful to not select any blob columns if you don't need it.

Also, you can't index an entire text column. You also can't sort using the entire content, only the first 200 characters.

It's a good idea to use the `VARCHAR` column for the first 1000 characters, and then if you need more, move on to `TEXT` or `MEDIUM`.

