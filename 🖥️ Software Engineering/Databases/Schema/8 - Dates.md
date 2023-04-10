If you just need a date, use `DATE`.

If you need time, you're looking between `DATETIME` and `TIMESTAMP`. Datetime is much larger (8 bytes versus 4). `TIMESTAMP` only works until `2038-01-19`.

However, MySQL tries to help you when working with timezones if you use `TIMESTAMP` by converting in and out the values for you.

Usually, it doesn't matter.