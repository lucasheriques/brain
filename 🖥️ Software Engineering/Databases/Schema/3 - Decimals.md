There are four (three, really) types of data types in MySQL that can store decimal values:
- `DECIMAL`, or its alias, `NUMERIC`: this is a fixed point, which means an exact value.
- `FLOAT` and `DOUBLE`: both are floating points, which means an approximate value.

If you need an exact representation of a number, you need to use the `DECIMAL`. If you're ok with an approximation (a good one, very close), then you can use `FLOAT` or `DOUBLE`.

If you are going to store currency, use `DECIMAL`.

When you're defining a `DECIMAL` column, you get to define how many digits there are and how many digits it has after the decimal point.

`d1 decimal(10,2)` means 10 digits before the decimal, and 2 after.