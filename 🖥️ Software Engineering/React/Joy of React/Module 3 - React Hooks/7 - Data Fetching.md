It's a good idea to have a `status` variable with potential 4 values: `idle`, `loading`, `success` or `error`.

How can we tell if a request succeeded? While it's possible to use status codes, that is unreliable. It's a good idea to use the server response to see if it went well.


for fetching on mount, it's a good idea to have a library like `SWR` or `@tanstack/query`, since those help with other features such as caching, revalidating data, etc.