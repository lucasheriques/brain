The `useIsOnscreen` hook allows us to pass in an element ref, and find out whether it's within the viewport:

```jsx
function App() {
  // Create a ref that holds a DOM node:
  // { current: <div> }
  const elementRef = React.useRef();

  // Pass it into `useIsOnscreen`, get back
  // a boolean value.
  const isOnscreen = useIsOnscreen(elementRef);

  return (
    <>
      <header>
        Red box visible: {isOnscreen ? 'YES' : 'NO'}
      </header>
      <div className="wrapper">
        {/* Capture a reference */}
        <div ref={elementRef} className="red box" />
      </div>
    </>
  );
}

```

The `useIsOffscreen` hook then uses that ref to set up an `IntersectionObserver`:

```jsx
import React from 'react';

function useIsOnscreen(elementRef) {
  const [isOnscreen, setIsOnscreen] = React.useState(false);

  React.useEffect(() => {
    const observer = new IntersectionObserver((entries) => {
      const [entry] = entries;

      setIsOnscreen(entry.isIntersecting);
    });

    observer.observe(elementRef.current);

    return () => {
      observer.disconnect();
    };
  }, [elementRef]);

  return isOnscreen;
}

export default useIsOnscreen;
```

To understand why this happens, we need to walk through how this works, step by step. The order of operations here is super important. Here's what happens:

1.  We create a new `elementRef` ref, which gets initialized to undefined.  
    `{ current: undefined }`
2.  We call the `useIsOnscreen` function, and pass this object in. The effect is _scheduled_, but doesn't run yet.
3.  We create a bunch of React elements, and return them from the `App` component
4.  As we saw in the [“Core React Loop” lesson](https://courses.joshwcomeau.com/joy-of-react/02-state/03.01-core-react-loop) [[2.1 - Core React Loop]]]], React will then produce a bunch of _real_ DOM nodes, using the React elements as a guide.
5.  After the DOM nodes have been created, our reference is captured, updating the `elementRef` object.  
    `{ current: <div> }`
6.  The effect we scheduled earlier runs, setting up the IntersectionObserver.

This component is only rendered once, and so the `useIsOnscreen` function is only called once. At the moment it's called, we don't yet have a reference to the DOM node, because that DOM node doesn't even exist yet!

But, because refs work by mutating an object, that doesn't matter; by the time the _effect_ runs, that object will have been edited to include the reference.

By contrast, when we try to pass the element directly (`useIsOnscreen(elementRef.current)`), we pluck the value _from_ the object. That value is `undefined`, at the time.
