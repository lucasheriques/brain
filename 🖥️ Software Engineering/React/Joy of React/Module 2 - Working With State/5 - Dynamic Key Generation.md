We can use something like `Math.random()` or `crypto.randomUUID()`, however, we need to be careful to do it once the object is being created.

If se use `Math.random` inside the rendered HTML, every time we change the state of the application, that same item is going to have to be rerendered. The reason for that is, even if not of the other properties of the item changed, its key changed. Which means, for React, that it is a brand new item.

Interacting with the DOM is one of the slowest things we can do in JS, so we wan't to do our best to minimize it.

# Array indexes as keys

Using indexes as keys works if the list is static. If the user is allowed to re-arrange items in the array, using the index can cause subtle, hard-to-diagnose bugs.