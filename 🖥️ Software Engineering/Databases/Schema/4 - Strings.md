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