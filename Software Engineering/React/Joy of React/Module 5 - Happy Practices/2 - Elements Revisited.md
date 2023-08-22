The createElement method creates a React element, a plain JS object. We're then storing a reference to this object in a variable, counterElem, and referencing that variable twice in the returned code.

```jsx
import React from 'react';

function App() {
  const counterElem = <Counter />;
  
  return (
    <div>
      {counterElem}
      {counterElem}
    </div>
  );
}

function Counter() {
  const [count, setCount] = React.useState(0);

  console.log(count);

  return (
    <button onClick={() => setCount(count + 1)}>
      {count}
    </button>
  );
}

export default App;
```

Consider this code. Even thought we have the same element being rendered, that don't share the same state. Each counter in independent.

**Creating an element doesn't mean that we're creating a component**. They're two entirely different things.

When we pass an element to React, we're giving it an sketch of how the component should look like. But, even if it's the same sketch, they will be different components.

**React elements are descriptions of something we want to create.**

As we go more granular in the tree, our object grows. See this example:

```jsx
const appSketch = {
  type: 'div',
  props: {},
  children: [
    {
      type: 'button',
      props: {
        onClick: function () {},
      },
      children: 0,
    },
    {
      type: 'button',
      props: {
        onClick: function () {},
      },
      children: 0,
    },
  ],
};
```

This is based on the code [within the lesson](https://courses.joshwcomeau.com/joy-of-react/05-happy-practices/02-elements).

Even if we have the same `counterElem`, which means it's the same reference to the object, it doesn't really matter. React never considers this. Instead, this singular description is used multiple times, to render multiple components.

The cool thing is that this kinda looks like the tree we see on the DOM:

```html
<div>
  <button>
    0
  </button>
  <button>
    0
  </button>
</div>
```

In earlier days, the React team used to call this the ***Virtual DOM***. Each component produces a chunk of JS that describes a slice of the application. By rendering components when we run into them, we can put all of those slices together and get a detailed sketch of the UI we want.

After doing all this work, React "commits" these changes by creating the necessary DOM nodes.

