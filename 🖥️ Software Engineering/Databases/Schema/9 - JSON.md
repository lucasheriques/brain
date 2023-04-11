**TLDR: While JSON columns can be a powerful addition to your MySQL schema, it's important to use them judiciously and in accordance with best practices. By following these guidelines, you can ensure that your use of JSON columns aligns with your broader schema design and helps you build more efficient and scalable applications.**

MySQL has first party support for JSON types.

When working with JSON data, MySQL is much more strict than with other text data types. The JSON data must be valid according to the JSON specification, or MySQL will reject it. This helps ensure that you're not storing incorrectly formatted data in your JSON columns.

Once you have valid JSON data in your MySQL database, you can use various functions and operators to retrieve and manipulate it.

Suppose we want to retrieve just the `key` from this JSON object. We could use the `->` operator, like so:

```sql
SELECT `json`->>"$.key" as key FROM has_json;
> key
> --------------
> value
```

The `->>` operator is used to extract a JSON object at a specific path. This is called the "JSON unquoting operator."

Indexes
---


One important consideration when using JSON columns in MySQL is that they cannot be directly indexed. Instead, MySQL supports indexing for generated columns on a specified JSON path. This means you can create an index on a specific key within a JSON object, but not on the entire object itself.

For example, consider the following code:

```sql
ALTER TABLE has_json ADD INDEX my_index ((`json`->>"$.key"));
```

Here, we're creating an index on the `key` field within the JSON object of our column. This allows MySQL to perform faster lookups for queries that involve this particular JSON path.

## [When and why to use JSON columns](https://planetscale.com/courses/mysql-for-developers/schema/json?autoplay=1#when-and-why-to-use-json-columns)
---
Before we wrap up, let's consider the best practices for storing JSON data in MySQL. While JSON columns in MySQL can be incredibly powerful, they should not be used as a replacement for traditional schema design! Instead, use JSON columns in situations where there is no well-defined schema or the schema changes frequently.

For example, a JSON column might make sense when you're storing payloads from third-party services or APIs that have different response formats. A JSON column can also be useful when you're storing nested or hierarchical data that doesn't fit neatly into a relational database design.

One caveat when using JSON columns is that they can be quite heavy, especially if you're storing large amounts of JSON data. As with any data type in MySQL, only select the data you need when you're querying, and avoid retrieving JSON data unnecessarily.
