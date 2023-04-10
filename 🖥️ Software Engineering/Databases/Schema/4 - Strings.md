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