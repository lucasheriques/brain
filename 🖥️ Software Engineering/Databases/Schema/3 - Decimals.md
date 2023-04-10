There are four (three, really) types of data types in MySQL that can store decimal values:
- `DECIMAL`, or its alias, `NUMERIC`: this is a fixed point, which means an exact value.
- `FLOAT` and `DOUBLE`: both are floating points, which means an approximate value.

If you need an exact representation of a number, you need to use the `DECIMAL`. If you're ok with an approximation (a good one, very close), then you can use `FLOAT` or `DOUBLE`.

If you are going to store currency, use `DECIMAL`.

