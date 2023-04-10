There are a bunch of different ways to store a string in MySQL. Here's a list of ways that we can use. For now, we're only covering `CHAR` and `VARCHAR`.

1. `CHAR`: fixed character. If you have any data that is truly of fixed length, this is the one you should use. That would be things like 2 digits, prefixes, maybe MD5 hashes. Something that is always gonna be the same size.
2. `VARCHAR`: stands for "variable character". 
3. `BINARY`
4. `VARBINARY`
5. `BLOB`
6. `TEXT`
7. `ENUM`
8. `SET`