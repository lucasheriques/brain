**TLDR: Migrations are a way to keep track of changes to a database schema, consisting of a folder full of SQL statements. They allow developers to make changes in a trackable, version-controlled, and maintainable way. Best practices for writing migrations include including explicit SQL statements, avoiding down migrations, and utilizing version control. Developers should also consider when to run migrations, as they can be expensive and take up significant resources. Managed platforms like PlanetScale offer a branch and merge process for running migrations without downtime. Overall, migrations are an essential component of database schema management that help developers manage and modify their database schema as business requirements change over time.**

## [The importance of migrations in database schema management](https://planetscale.com/courses/mysql-for-developers/schema/schema-migrations?autoplay=1#the-importance-of-migrations-in-database-schema-management)

As developers, we know that as business requirements change we need to make changes to our database schema accordingly. But how can we keep track of these changes? How can we make sure our development team is on the same page with these changes? This is where the concept of migrations comes into play.

### [What are migrations?](https://planetscale.com/courses/mysql-for-developers/schema/schema-migrations?autoplay=1#what-are-migrations)

At their most basic, migrations are a folder full of SQL statements that help keep track of changes to your database schema. Most full-stack frameworks have a migrations concept, which allows developers to easily and efficiently make changes to their schema. Migrations allow developers to make changes in a trackable, version-controlled, and maintainable way.

Regardless of which web framework you are using, the concept of migrations remains the same: they help developers make changes to their schema in a trackable and maintainable way.

### [Best practices for migrations](https://planetscale.com/courses/mysql-for-developers/schema/schema-migrations?autoplay=1#best-practices-for-migrations)

When it comes to writing migrations, it's best to agree with your team on the best practices for _your_ team. Here are a few you might consider:

-   Always include explicit SQL statements to show how the database will move from one state to another.
-   Avoid using down migrations, which can lead to issues if the down method doesn't completely undo what the up method did.
-   Utilize version control to keep track of changes to your schema over time.

Additionally, developers should consider when to run migrations, as they can be expensive and take up significant resources. Options for running migrations include scheduled maintenance windows or using tools like `pt-online-schema-change` or `gh-ost` (GitHub online schema change.)

Managed platforms like PlanetScale also offer a branch and merge process for running migrations without downtime.

Migrations are an essential component of database schema management that help developers make changes to their schema in a trackable and maintainable way. By following best practices and understanding when to run migrations, developers can successfully manage and modify their database schema as business requirements change over time.