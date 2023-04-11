**TLDR: Enums in MySQL are a powerful feature that can simplify database design, increase security, and improve readability. With a predefined list of allowable values for a column, the benefits of enums are clear. However, it's also important to keep in mind the limitations and potential drawbacks of using enums, such as the need to alter the schema if allowable values change. Overall, if used correctly, enums can be a valuable tool when working with string data in MySQL.**

Enums have lots of advantages: readability of a string, little bit of data validation and storage-level of integers.

However, they do have some drawbacks:

1. sorting are made with the underlying integer value.
2. you can't add another option without changing the whole schema.

please don't ever use integer enums, just use a `TINYINT` column.


Fixed number of options that don't really change is the best use case for enums.


## [Benefits of enums](https://planetscale.com/courses/mysql-for-developers/schema/enums#benefits-of-enums)

Using enums in MySQL has several benefits, including:

### [Data validation](https://planetscale.com/courses/mysql-for-developers/schema/enums#data-validation)

As mentioned earlier, enums offer data validation, which helps to ensure that only valid data is entered into a column. When attempting to enter an invalid value, an error is thrown, preventing the data from being inserted into the database.

### [Readability](https://planetscale.com/courses/mysql-for-developers/schema/enums#readability)

Since enums allow you to store readable values in your database, it's easier to read the stored data at a glance. You don't need to memorize integers to understand the data; the values make sense in plain English.

### [Compact data type](https://planetscale.com/courses/mysql-for-developers/schema/enums#compact-data-type)

Enums are compact data types, which means they take up less storage space than other data types, such as strings. This feature makes them ideal for databases with large amounts of data.

## [Downsides of enums](https://planetscale.com/courses/mysql-for-developers/schema/enums#downsides-of-enums)

While enums offer several benefits, there are some downsides to using them, including:

### [Changes to the schema](https://planetscale.com/courses/mysql-for-developers/schema/enums#changes-to-the-schema)

If a business requirement changes, and you need to add another option to the allowable values, you'll have to alter the schema of your table to add a new enum. While this process is not difficult, it can be inconvenient.

### [Ordering](https://planetscale.com/courses/mysql-for-developers/schema/enums#ordering)

When sorting data using enums, MySQL sorts by the underlying integer value rather than the actual string. While this can be useful in some cases, it can also be quite confusing, especially if you're not expecting it.

### [Using integer enums](https://planetscale.com/courses/mysql-for-developers/schema/enums#using-integer-enums)

Finally, it's important to note that integer enums can be confusing and should be avoided if possible. If you must use integer enums, it's best to use a `TINYINT` column instead.