**TLDR: Writing a schema is crucial and requires selecting small, simple, and honest data types. Schema designs matter because they affect database performance and indexing efficiency. Choosing a compact schema can improve index speed and efficiency, as well as make the database faster to access.**

This is the first opportuntity to set ourselves up to success or failure.

Schema is really: what are our tables? How do we define them? What are their attributes? etc

## Writing a schema

You can write the definitions by hand, or just let your framework generate them. Usually we just let the framework do it for us. However, it's imperative to remember that, ultimately, we are the ones responsible for the schema, regardless of how we create it.

MySQL has lots of different data types, but, when writing a schema, it's important to keep three principles in mind when choosing one:

1. **Small**: Pick the smallest data type that will hold all of your data.
2. **Simple:** Pick the simplest column type that accurately reflects your data (e.g. use a numeric type for numbers, not a string).
3. **Honest**: the schema should reflect reality. If some data is not nullable, do not make it nullable. Extract the correct schema from the shape of your data.


## Why schema designs matter

Disks are cheap, yes, but we're not optimizing for compactness so we can buy smaller disks. We do it so it fits better on the disk, and the database can access it faster. The more compact it is, the faster the DB can access it.

Also, when it comes to create indexes, a compact schema can improve index speed and efficiency. This is because indexes are stored in memory, and a smaller schema means less memory usage.

## Colu