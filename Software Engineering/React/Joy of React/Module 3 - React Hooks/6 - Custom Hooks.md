With Custom Hooks, we're able to share custom business logic between components.

```js
function Clock() {
  const time = useTime();

  return (
    <p className="clock">
      {format(time, 'hh:mm:ss a')}
    </p>
  );
}

function useTime() {
  const [time, setTime] = React.useState(
    new Date()
  );

  React.useEffect(() => {
    // Effect logic
    const intervalId = window.setInterval(() => {
      setTime(new Date());
    }, 1000);

    return () => {
      // Cleanup logic
      window.clearInterval(intervalId);
    };
  }, []);

  return time;
}
```

Take the above code for instance. With the new custom hook, we're able to `useTime` on any component we want.

The main advantages of custom hooks are these:

1. Code organization - we're able to better separate the concerns between UI and business logic.
2. Code reuse - the business logic/function can now be shared between any components.

The one exception about React's *Rules of Hooks* regarding usage is that we can use React hooks on custom hooks. We can identify custom hooks by naming the function `use{...}`.


# Memoization addendum

When creating custom hooks that might be used everywhere, it's a good idea to memoize any functions that we create as a part of them, because you never know where on the tree you might be using it.