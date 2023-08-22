No need to pick up a npm package. Just use the `new Intl.NumberFormat()`. It's very good and built in into the browser.

```js
  const formattedPrice = new Intl.NumberFormat('en-US', {
    style: 'currency',
    currency: 'USD',
  }).format(price);
```