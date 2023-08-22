**TLDR: When working with decimal values in MySQL, it's important to choose the correct data type for your needs. If you require absolute precision in your values, `DECIMAL` is the best choice. If you don't require exact values, `FLOAT` or `DOUBLE` may be more appropriate. Which one you choose just depends on the range of data you're storing and the amount of precision you need.**

**Remember, when working with `FLOAT` or `DOUBLE`, results will not be exactly precise, and values may be slightly different from what you expect.**

There are four (three, really) types of data types in MySQL that can store decimal values:
- `DECIMAL`, or its alias, `NUMERIC`: this is a fixed point, which means an exact value.
- `FLOAT` and `DOUBLE`: both are floating points, which means an approximate value. `FLOAT` is 4 bytes, `DOUBLE` is 8 bytes.

If you need an exact representation of a number, you need to use the `DECIMAL`. If you're ok with an approximation (a good one, very close), then you can use `FLOAT` or `DOUBLE`.

If you are going to store currency, use `DECIMAL`.

When you're defining a `DECIMAL` column, you get to define how many digits there are and how many digits it has after the decimal point.

`d1 decimal(10,2)` means 10 digits before the decimal, and 2 after. Keep this in mind when you're defining the column.

