**TLDR: In conclusion, `BINARY` and `VARBINARY` columns in MySQL provide an efficient way to store binary data that may not have a valid string representation. Using binary columns, you can store hash and UUID data more compactly on disk, without the need for character sets and collations. Although these columns may not be widely used, they can be essential for storing data in certain use cases.**


3. `BINARY`: fixed.
4. `VARBINARY`: variable.x

Instead of storying characters, binary and varbinary store bites only. No character set, no collations. You can use these columns to store little bits of binary data that can't be represented as regular strings or don't need to be.

The `BINARY` column is a fixed length column, while the `VARBINARY` column is a variable length column. With `VARBINARY` columns, you can store up to a set number of bytes, rather than fixed data types. Although not too commonly used, `BINARY` and `VARBINARY` columns provide an efficient way to store binary data, such as hashes or UUIDs.
