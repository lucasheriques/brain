**TLDR: Understanding the different types of columns that can hold integer values and their respective ranges is crucial to designing a database schema that's both efficient and scalable. By selecting the appropriate data type for each column, we can avoid unnecessary storage requirements and ensure efficient queries.**

There are 5 different types of data types that can be used to store integers (if you see any others, they're probably aliases):

| Type        | Storage (Bytes) | Minimum Signed | Minimum Unsigned | Minimum Unsigned | Maximum Unsigned |
| ----------- | ---------------:| --------------:| ----------------:| ----------------:| ----------------:|
| `TINYINT`   |               1 |           -128 |              127 |                0 |              255 |
| `SMALLINT`  |               2 |         -32768 |            32767 |                0 |            65535 |
| `MEDIUMINT` |               3 |       -8388608 |          8388607 |                0 |         16777215 |
| `INT`       |               4 |    -2147483648 |       2147483647 |                0 |       4294967295 |
| `BIGINGT`   |               8 |          -2^63 |           2^63-1 |                0 |           2^64-1 |

`TINYINT` occupy 1 byte, which is 8 bits.

- `00000000` = 0
- `11111111` = 255

If you want to support negative numbers, one of the bits is dedicated to the sign (signed data type).

- `0 1111111` = -128 (negative bit)
- `1 1111111` = 127 (positive bit)

## [Common misconception: `INT(11)`](https://planetscale.com/courses/mysql-for-developers/schema/integers?autoplay=1#common-misconception-int11)

It's common to see something like `INT(11)` and assume that the `11` controls the range of data that can be stored. However, the number in parentheses has no effect on the underlying storage or the range of the column. This notation was only ever intended to define a display width. It is deprecated and will be removed soon.