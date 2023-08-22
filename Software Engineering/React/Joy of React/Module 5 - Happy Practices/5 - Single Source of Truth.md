Earlier when we were talking about forms, we saw that an input can be either *controlled* or *uncontrolled.*

A controlled input is boung to React state. An uncontrolled input, however, is bound to the internal DOM state.

A similar rule can also be applied to *components* we create. Consider this:

```jsx
function Counter() {
  const [count, setCount] = React.useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      {count}
    </button>
  );
}

function App() {
  return (
    <Counter />
  );
}
```

This *Counter* component is independent. From the consumer perspective, `Counter` is totally self-contained. It has its own internal state, and you can't access it. It's like an **uncontrolled input**.

```jsx
function App() {
  const [count, setCount] = React.useState(0);

  return (
    <Counter
      count={count}
      onIncrement={() => setCount(count + 1)}
    />
  );
}

function Counter({ count, onIncrement }) {
  return (
    <button onClick={onIncrement}>
      {count}
    </button>
  );
}
```

Now, if we re-write it, this new version is controlled by the consumer. Like a controlled text input. It's not the exactly same way, however, from the perspective of the consumer, it's similar.

**The most important thing about this is that there should be always a single source of truth.** We can run into all kinds of bugs if we start treating a component as both controlled and uncontrolled.

Further reading: [You Probably Don't Need Derived State](https://legacy.reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html). Unfortunately, this post is from 2018, and so all of the examples use class-based components. But I think the core ideas are still just as relevant today, and hopefully it's relatively clear!