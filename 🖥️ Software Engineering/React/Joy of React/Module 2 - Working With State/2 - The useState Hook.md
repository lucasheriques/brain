# Initial value

State variables can be given an initial value, like `React.useState(1)`, which will initialize the state with the value 1.

We can also supply a **function**. React will call this function on the very first render to calculate the initialValue:

```js
const [count, setCount] = React.useState(() => {
  return 1 + 1;
});

console.log(count); // 2
```

This secondary form is useful if we're doing an expensive operation to calculate the initial value, for instance, reading from localStorage:

```js
const [count, setCount] = React.useState(() => {
  return window.localStorage.getItem('saved-count');
});
```

The benefit is that we're only doing the expensive work (reading from storage) once, on the initial render, rather than doing it on every single render.

When we pass a function to `React.useState`, its up to React what to do with it. On the very first render, React will call the function to calculate the initial value. On *subsequent* renders, however, React ignores the function, since the initial value was calculated already.



---


[[2.1 - Core React Loop]]

# Asynchronous updates

State setters are not immediate.

When we call a `setX` function, we tell React we'd like to schedule a change to a state variable. Then, React waits until the current operation is completed (let's say, a button is clicked), and then it updates the value and trigger the re-render.

If you need the value beforehand, add it to a variable so you can access it whenever.

```js
function App() {
  const [count, setCount] = React.useState(0);

  return (
    <>
      <p>
        You've clicked {count} times.
      </p>
      <button
        onClick={() => {
          const nextCount = count + 1;
          setCount(nextCount);

          console.log(nextCount)
        }}
      >
        Click me!
      </button>
    </>
  );
}
```