React uses keys to uniquely identifying each DOM element.
Whenever a key changes, the DOM node will change. Maybe it'll move around, maybe it'll get deleted, maybe a new one will be added.

---
Keys allow React to connect to a specific ID with a specific React element and the associated DOM. When the data changes, React uses the keys to work out what DOM manipulation is required (wether we edit the contents of a DOM node, reorder the node, or destroy/recreate it).

Whenever the key changes, we're telling React that the DOM node it's tied to no longer exists and has been replaced by a new element. So React will go and delete the node with the previous key, and it'll create a brand new one to replace it.

---
If the key changes, the component will be unmounted, which removes any DOM associated with it, and then remounted. Fortunately, this isn't a big deal from a performance perspective, because components instances are designed to be pretty disposable and to be quick to create.

So we can absolutely use keys with this way.

---

There's two ways to change the key for a given component:

```js
<PriceDisplay
  key={plan.id}
  price={plan.price}
/>
```

```js
<PriceDisplay price={plan.price} id={plan.id} />

function PriceDisplay({ id, price }) {
  const formattedPrice = new Intl.NumberFormat('en-US', {
    style: 'currency',
    currency: 'USD',
  }).format(price);

  return (
    <div className={styles.wrapper} key={id}>
      <div className={styles.animated}>
        {formattedPrice}
      </div>
    </div>
  );
}

export default PriceDisplay;
```

In tems of performance, they're both pretty similar, as running the `Intl` API is quick. So that is not the concern.

However, the question is: should `PriceDisplay` always animate/destroy&recreate if the price changes? If so, it's probably a good idea to embed this behavior on the component. But, if we want to give more control to the consumer of the component, we can lift the key property up to the `<PriceDisplay>` element.

Further reading: [You Might Not Need an Effect](https://react.dev/learn/you-might-not-need-an-effect).
