Context provides an easy way to access data without having to prop drill it.

It has two benefits:

- You don't need to keep passing an unused prop on the tree if only a leaf component uses it
- Makes maintenance easier, since you can easily remove or add props from it, without having to update all components in the tree that used this data

# Syntax

Let's suppose we have a `favouriteColor` held in state, and we want to make it available to every component in the application, using context.

There are two steps: **providing** and **consuming**.

## Step 1: Providing

We use a ***provider*** to make a particular value available through context. We do this by wrapping our application in a Provider component, which we get from React when creating a context.

```jsx
// App.js
import React from 'react';

import Home from './Home';

// Create a new context
export const FavouriteColorContext = React.createContext();

function App() {
  const [
    favouriteColor,
    setFavouriteColor
  ] = React.useState('#EBDEFB');

  // Wrap everything `App` would normally render inside
  // a Provider, and pass our `favouriteColor` state
  // variable as the value:
  return (
    <FavouriteColorContext.Provider value={favouriteColor}>
      <Home />
    </FavouriteColorContext.Provider>
  );
}

export default App;
```

A context can be thought as a channel, a radio frequency we can use to broadcast data down through the app.

More concretely, `FavouriteColorContext` is a plain old JavaScript object. It includes a bunch of stuff that React uses internally. It also includes a `Provider` component for us to render.

When we render `<FavouriteColorContext.Provider>`, we start broadcasting a value, making it available to any descendant component. In this case, we're broadcasting the `favouriteColor` state variable.

Often, Provider componts are kept at the very top of our application, so that their broadcast can reach anywhere in the app.

## Step 2: Consuming

```jsx
import { FavouriteColorContext } from './App';

function Sidebar() {
  const favouriteColor = React.useContext(FavouriteColorContext);
}
```

`useContext` is a hook designed to "plug in" to a particular context and pluck out its current value.

**Basic formula**:

1. Create a new context with `React.createContext`.
2. Use the `Provider` component, from that context, to wrap around the application. Pass it a bundle of values that you need in other pats of the app.
3. Pluck the data you need from context, with the `useContext` hook.

**Josh's rule of thumb**: if I find I keep having to pass a prop *through* a component, I should probably use context for it.

For example, consider this component:

```jsx
function AccountSettings({ user }) {
  return (
    <section>
      <UserProfile user={user} />
    </section>
  )
}
```

The AccountSettings component doesn't actually use the user prop, it passes it right along to UserProfile.

I don't mind doing this sometimes, but if I find I keep having to pass a specific prop along, it's a sign that I should probably switch to context.

This is the strategy that works best for me, but this is subjective, and there's no right/wrong answer!

# Provider Components

Instead of trying to group a multitude of information within the same context, it's an established best practice to create individual contexts for each discrete concern.

- There are potential performance benefits.
- It can improve code readability.

To do that, we can use something called the ***provider component pattern***.

We'll create individual components for each provider, and this component will manage everything related to that context.

Here's an example of an app using this pattern:


```jsx
import Homepage from './Homepage';
import UserProvider from './UserProvider';
import ThemeProvider from './ThemeProvider';
import PlaybackRateProvider from './PlaybackRateProvider';

function App() {
  return (
    <UserProvider>
      <ThemeProvider>
        <PlaybackRateProvider>
          <Homepage />
        </PlaybackRateProvider>
      </ThemeProvider>
    </UserProvider>
  );
}
```

# Performance

The thing to remember is: whenever we pass an object as the value attribute in a context provider (most of the times), we want to memoize that object so that we're only regenerating it when one of the properties on the object changes.

Also: **we can't memoize components that receive React Elements as props** (usually children, but can be any component really). Because React Elements are just JavaScript objects (or arrays if there are multiple elements), that means that they'll regenerate on every render.

```js
// Simplified return of React.createElement
{
  $$typeof: Symbol(react.element),
  type: ƒ Counter,
  props: { count, setCount },
},
```

This stuff is funky as heck, but here's the takeaway: **When it comes to context providers, we should memoize the `value`. We can't memoize the component itself.**[]()