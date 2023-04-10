**TLDR: When it comes to storing time-related data in MySQL, it's essential to choose the right data type based on your needs. The `DATE`, `DATETIME`, and `TIMESTAMP` data types are the most commonly used, with `TIMESTAMP` being the most compact and efficient way to store date _and_ time data.**

**When choosing between `DATETIME` and `TIMESTAMP`, consider storage size, the range of data needed, and how time zones are handled. Ultimately, utilizing MySQL effectively for storing and handling temporal data can help your application function efficiently and accurately.****

If you just need a date, use `DATE`.

If you need time, you're looking between `DATETIME` and `TIMESTAMP`. Datetime is much larger (8 bytes versus 4). `TIMESTAMP` only works until `2038-01-19`.

However, MySQL tries to help you when working with timezones if you use `TIMESTAMP` by converting in and out the values for you.

Usually, it doesn't matter.

For the other types, `YEAR` and `TIME`, they're not used often, but you should be aware of them.

### [`DATE`](https://planetscale.com/courses/mysql-for-developers/schema/dates?autoplay=1#date)

If you only need to store the date, then the `DATE` type column is your best bet. It is a three-byte data type that can store a vast range of data from the year 1,000 to 9,999.

### [`DATETIME`](https://planetscale.com/courses/mysql-for-developers/schema/dates?autoplay=1#datetime)

If you need to store both the date and time, then `DATETIME` and `TIMESTAMP` are the two options you have. `DATETIME` is an eight-byte data type that can store a massive range of data. So, if you need to store time data up to the year 9,999, `DATETIME` is the way to go.

### [`TIMESTAMP`](https://planetscale.com/courses/mysql-for-developers/schema/dates?autoplay=1#timestamp)

`TIMESTAMP`, on the other hand, is a four-byte data type that can store a more limited range of data, from the year 1970 to 2038-01-19. This limitation is referred to as the "2038 problem." If you only need to store time data within this range, `TIMESTAMP` is the more compact and efficient option.

### [`YEAR`](https://planetscale.com/courses/mysql-for-developers/schema/dates?autoplay=1#year)

If you need to store a year between 1901 and 2155, `YEAR` would be the most compact way to do it. This type is not very commonly used.

### [`TIME`](https://planetscale.com/courses/mysql-for-developers/schema/dates?autoplay=1#time)

The `TIME` data type is used to store hours, minutes, and seconds. It can store more than 24 hours, which is useful for storing intervals. This type is useful for a 10-day range denominated in hours, minutes, and seconds, but it's not commonly used.

---

## [Choosing between `DATETIME` and `TIMESTAMP`](https://planetscale.com/courses/mysql-for-developers/schema/dates?autoplay=1#choosing-between-datetime-and-timestamp)

If you need to store both the date and time, you'll need to choose between `DATETIME` and `TIMESTAMP`. Both data types have their advantages and disadvantages, so it's essential to understand the differences between the two.

### [Storage size](https://planetscale.com/courses/mysql-for-developers/schema/dates?autoplay=1#storage-size)

The first difference between `DATETIME` and `TIMESTAMP` is storage size. `DATETIME` is an eight-byte data type, while `TIMESTAMP` is a four-byte data type. This makes `TIMESTAMP` more compact and more efficient in terms of storage space.

### [Range of data](https://planetscale.com/courses/mysql-for-developers/schema/dates?autoplay=1#range-of-data)

The second difference between these two data types is the range of data they can store. As mentioned earlier, `DATETIME` can store time data up to the year 9,999. In contrast, `TIMESTAMP` can store data only from 1970 to 2038.

Due to this limitation, you may have to use `DATETIME` in cases where you need to store data beyond 2038.

### [Time zones](https://planetscale.com/courses/mysql-for-developers/schema/dates?autoplay=1#time-zones)

One final difference between `DATETIME` and `TIMESTAMP` is how they handle time zones. With `DATETIME`, MySQL does not handle time zones at all. Whatever you put in, you get back out. With `TIMESTAMP`, MySQL tries to help you by converting values to UTC when added to the database and back to your time zone when retrieved.

This difference is essential to consider when choosing between these two data types, especially if your application requires handling different time zones.