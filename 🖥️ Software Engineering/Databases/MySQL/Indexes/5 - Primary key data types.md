**TLDR: The primary key serves as a unique identifier for each record in a table, and it is essential to choose the right data type for it when designing a database schema. The recommended data type for primary keys in MySQL is unsigned big integers because they provide virtually infinite room to grow and allow for auto-incrementing. Choosing strings as primary keys, such as UUIDs or GUIDs, can lead to potential pitfalls due to their size, which can cause indexes to grow enormously, and B-trees may have to be rebalanced if insertions occur in the middle of the table. If using a string data type as a primary key, it is best to choose a UUID or GUID that is time-sorted to keep new records at the end of the table. Obfuscating primary keys for public APIs or URLs with UUIDs or GUIDs is not recommended. Ultimately, selecting the right data type for primary keys will depend on the database's specific needs and how it is designed, but it is essential to evaluate associated pitfalls to ensure proper usage.**

# [What data type you should use for primary keys in MySQL](https://planetscale.com/courses/mysql-for-developers/indexes/primary-key-data-types?autoplay=1#what-data-type-you-should-use-for-primary-keys-in-mysql)

An essential decision when designing a database schema is choosing the data type for the primary key. The primary key serves as a unique identifier for each record in a table, and it is a critical element in database design. As such, it is essential to choose the right data type that meets the database's requirements and avoid potential pitfalls that could lead to performance issues or other problems down the road.

## [The benefits of unsigned big integers](https://planetscale.com/courses/mysql-for-developers/indexes/primary-key-data-types?autoplay=1#the-benefits-of-unsigned-big-integers)

The recommended practice for primary keys is to use unsigned big integers. Unsigned big integers provide virtually infinite room to grow, which is essential because running out of primary key space is a significant issue for databases. Additionally, they allow for auto-incrementing, which preserves a natural order for the records, ensuring that the primary key B-tree isn't split unnecessarily.

## [Choosing strings as primary keys](https://planetscale.com/courses/mysql-for-developers/indexes/primary-key-data-types?autoplay=1#choosing-strings-as-primary-keys)

Choosing a string data type, such as a UUID or a GUID, as a primary key can be tempting, but it has potential pitfalls. The problem with these types of data is their size, which means the indexes of the table grow enormously as a result of them. Additionally, the B-tree may have to be rebalanced if insertions occur in the middle of the table.

If you want to use a string as a primary key, you should look for a UUID or GUID that is time-sorted, so all new records go to the end of the table, rather than in the middle. ULIDs are a new option for sorted GUIDs that are worth considering.

## [Obfuscation of the primary key](https://planetscale.com/courses/mysql-for-developers/indexes/primary-key-data-types?autoplay=1#obfuscation-of-the-primary-key)

Some developers might use UUIDs or GUIDs to obfuscate the primary key when exposed in public APIs or URLs. This approach is not ideal, as the primary keys are better used for unique identification of each record in the database while leaving the obfuscation to a separate column.

## [Conclusion](https://planetscale.com/courses/mysql-for-developers/indexes/primary-key-data-types?autoplay=1#conclusion)

Ultimately, the choice of data type for primary keys will depend on the database's specific needs and how it is designed. However, it is worth noting that unsigned big integers are the most reliable and performant data type to use,. While other types are valid options, associated pitfalls must be evaluated to ensure proper usage.

So keep in mind that selecting the right data type can prevent future headaches and allow for an efficient and easily scalable database.