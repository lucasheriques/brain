- When our React app modifies state, we can't modify the array directly. This leads to bugs.
- This is because React uses *referencial equality* (values have the same memory address) to see if state has changed or not. Mutating an array does not produce a new array.
- We can fix that by using a brand-new array, using the `...` spread syntax.

**Never mutate React state, even if it works.** This might lead to obscure bugs that might be hard to track.

**What about the performance of constantly cloning arrays?**

Cloning arrays is really fast, so no need to worry about that. On a very slow computer, it takes about 2ms to clone a new array a thousand times.

However, if your array had millions of items, it could take longer. But, we generally don't work with big arrays on the front-end, because the data would take way too long to transfer over the network, and low-end devices would not have the memory to hold it. **Iteration speed is rarely the limit factor on the front-end**.

It's a good idea to test your intuition about this. If you find yourself wondering if a piece of code is fast, give it a quick test. You can use a simple snippet like this:

```js
const start = Date.now();

// expensiveFunction();

console.log(Date.now() - start); // will return how many ms the function took
```

Modern JS engines are blazing fast, even on low-end devices. When it comes to performance on the front-end, we have bigger things  to worry about.