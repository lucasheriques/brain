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

If you want to support negative numbers, one of the bits is dedicated to the sign.

- `0 1111111` = -128 (negative bit)
- `1 1111111` = 127 (positive bit)

