# useState

You call `useState` with the initial state value, and it returns an array with the value of that state and a mechanism for updating it (called "state `dispatch` function).

When you call the state dispatch function, you pass the new value for the state and that triggers a re-render of the component which leads to `useState` getting called again to retrieve the new state value and dispatch function again.

## Lazy initialization

When the `initialState` is something computally intensive, we can pass a function to the initialState, and by doing that, React will only call the function when it needs the initial value (which is when the component is initially rendered).

```js
const getInitialState = () => Number(window.localStorage.getItem('count'))

2const [count, setCount] = React.useState(getInitialState)
```

