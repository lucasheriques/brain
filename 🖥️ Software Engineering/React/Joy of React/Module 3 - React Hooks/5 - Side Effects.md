 When building applications, we sometimes need to request data from external systems. Some examples are:
- Making network requests
- Managing timeouts / intervals
- Reading/writing from localStorage
- Listening for global events

React calls this things **side effects**.

# About best practices

We should always strive to get better, and it helps if you follow the best practices. However, it's not a matter of life and death. Sometimes, you're going to write some code that will not follow the best practices, and that is okay.

The important part here is to be always learning. If you get to the point where you look at the code you wrote an year ago and don't feel embarrassed, that's when you need to worry. Because it means stagnation.

As a senior engineer, you have written code that **became technical debt**. And, because of those experiences, you can strive to be better in the future. You already experienced it - now, do your best to avoid it. Following best practices is a good way to do that.

# The useEffect hook

We've been talking about this thing that React does that we're calling [[2.1 - Core React Loop]].

It starts with providing React a chunk of JSX, which tells a description of what we want to show it on the DOM. When the user does something that triggers a state change, it re-runs that JSX giving new values that are relevant.

This is React's main job.

However, every now and then, we need to do things that are outside this loop. For instance, social networks try to update the title of the window when you get a new notification. To do that, you need to perform a side effect.

**Side effects** occurs when you want to do something that is outside of React typical responsibilities, but it still needs to be synchronized with React internal state.

The way to perform those effects is by using the `React.useEffect` hook.

```js
React.useEffect(() => {
	document.title = `${pieceOfState} - Updated Title`;
})
```

Whenever React wants to update any kind of data (prop, state, something changed), it'll first do its job, and execute every code inside the function, then returning the JSX. After that, it'll call the function we gave it, in the example above, updating the document title.

We can also pass an array of dependencies to the useEffect hook. What it effectively does is: it'll only call the function if any value of the dependancy array changed.

```js
React.useEffect(
  () => {
	document.title = `${pieceOfState} - Updated Title`;
  },
  [pieceOfState]
)
```

Now, this function will only execute if `pieceOfState` changed.

The effect will only execute **after the first render**, no matter what.

The **useEffect** hooks is designed to solve a very specific problem: synchronize the React state with something that exists outside of React (maybe a database, or the user scroll position).[s]()

# Strict mode gotcha

When using *Strict Mode*, React will automatically re-run certain chunks of code. This is done to highlight potential issues.

# Debug hint

Let's say you are debugging a piece of state. You might just write something like `console.log({pieceOfState})`, and that is just fine.

However, your console might get spammed because this code will run every time the component rerenders.

A tip is to wrap it in a effect:

```js
useEffect(() => {
  console.log({pieceOfState});
}, [pieceOfState])
```

This way, we'll only print to the console if the relevant state changes.

# Effect Lint Rules

Assume we have this code:

```js
function App() {
  const [count, setCount] = React.useState(0);

  React.useEffect(() => {
    console.log(count);
  }, []);

  return (
    <>
      <p>The count is: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </>
  );
}
```

If we run this code as is, we'll get a lint warning from React that we're violating the rule `react-hooks/exhaustive-deps`. There are people that will say a solution to that is to just add this piece of magic:

```js
React.useEffect(() => {
  console.log(count);
  // eslint-disable-next-line
}, []);
```

That disables the rule, however, doesn't solve the underlying problem.

Remember that once we set state, we're assigning it to a memory address in our computer. If we don't include the `count` in the dependency array, we'll have a very weird situation: our `count` inside the state will have the old reference to the state (to another address in the memory). What it means is that `count` inside the effect is effectively *frozen in time*. It'll only have access to the first `count` variable, which is equal to `0`.

To fix it, we need to add `count` to the dependency array, which means that the effect will re-run whenever we call `setCount`, keeping the effect in sync with state changes.


```js
React.useEffect(() => {
  console.log(count);
  // eslint-disable-next-line
}, [count]);
```

> PS: sometimes, we need to access the freshest "version" of the state but we don't want the effect to re-run whenever it changes. See more about it at [[5.1 - Effect Cleanup]].

# Running on Mount

We can just use an `useEffect` with an empty dependency array.

By default, `useEffect` runs after every single render. However, that is not what we want every time.

```js
React.useEffect(() => {
  // perform effect
}, []);
```

> The one unavoidable thing about effects is that they always run after the initial mount. Since we're passing an empty array, that will never change, that just means that this m effect will only run a single time: after the initial time.

# Effect Cleanup
[[5.1 - Effect Cleanup]]

# Early returns

Consider this two effects:

```js
  React.useEffect(() => {
    if (isOn) {
      return;
    }

    const timeout = window.setTimeout(() => {
      console.log('turn on again');
      setIsOn(true);
    }, 1 * 500);

    return () => {
      clearTimeout(timeout);
    };
  }, [isOn]);


React.useEffect(() => {
  if (!isOn) {
    const timeoutId = window.setTimeout(() => {
      setIsOn(true);
    }, 500);

    return () => {
      window.clearTimeout(timeoutId);
    };
  }
}, [isOn]);
```

They both accomplish the same thing: changing `isOn` to true if it is false, after 500ms. However, the early return is preferable.

A well designed effect should have one single purpose. In this case, the purpose is to set `isOn` to true in case it becomes `false`.

But using the early return, we can emphasize on the effect **primary purpose**. We can clear away the conditions, so they dont obfuscate the primary purpose.

This pattern is useful for all kins of functions, not just React effects. And, when using it consistently, it makes it so much easier to quickly understand what is a function doing.


```js
// Option 1
async function logInUser(email, password) {
  const user = await findUser(email);

  if (user) {
    const isValidPassword = await validatePassword(user, password);

    if (isValidPassword) {
      await logInUser();
      return { user };
    } else {
      return { error: 'invalid password' };
    }
  } else {
    return { error: 'user not found' }
  }
}

// Option 2
async function logInUser(email, password) {
  const user = await findUser(email);

  if (!user) {
    return { error: 'user not found' }
  }

  const isValidPassword = await validatePassword(user, password);
  if (!isValidPassword) {
    return { error: 'invalid password' };
  }

  await logInUser();
  return { user };
}
```

The primary goal of this function is to log the user in. In option 1, that goal is focused in the middle of the function. However, in option 2, this structure is flattened, returning as soon as we can. And, we can easily skip to the bottom to see the function's primary purpose.

# React Strict Mode

TLDR: strict mode makes everything run twice (effects and renders)). If runs the effect, then the clean up function, then the effect again.

The goal with that is to ensure our application is working as intended, without any memory leaks. If something happens, it'll make it easier to notice.

It has no effect on production.

### Strict Mode vs manually rerendering a component

Strict Mode makes the effect run twice on the same component instance.

When you unmount a component, you're destroying that instance. So, when it's rendered again, it's a whole new instance.