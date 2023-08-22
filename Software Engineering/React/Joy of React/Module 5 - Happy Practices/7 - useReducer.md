With `useReducer`, we're separating our state into two separate ideas:

1. The actions that fire in our application, like the user adding a new todo, or marking a todo as completed.
2. The state-updating logic that runs when an action occurs.

In this video, I demonstrate how `useReducer` works by migrating our Todo list application to use `useReducer` instead of `useState`. It's a difficult video to fully summarize, but essentially we:

-   Create a `reducer` function to hold all of the state-updating logic
-   Use the `dispatch` function to tell React when an action occurred
-   Update the 3 bits of business logic — creating a todo, toggling a todo, and deleting a todo — to use this new flow.

The drawback of useReducer is that there's more scaffolding required. We have to jump through a couple of hoops.

The benefit is that it forces us to group our state-updating logic together. There is no setTodos function; the only way to change the todos state is to dispatch an action.

Also, because the reducer function lives outside our component, we can easily set up unit tests without requiring us to mount any components.

Essentially, useReducer presents an alternative structure we can use for our state-updating logic. It may not be worth the boilerplate in simple cases, but it does nudge us towards a good structure, and this can really help in complex situations.

Also, reducers must be pure functions, which means, it always returns the same output given the same inputs.

```js
// example of pure function - addNums(1,1) returns 2 every time
function addNums(a, b) {
  return a + b;
}

// example of impure function - it generates a different result every time it's called
function getRandomNumber() {
  return Math.random();
}
```

**Why do reducers need to be pure?**
[Original lesson](https://courses.joshwcomeau.com/joy-of-react/05-happy-practices/07-use-reducer).

In the playground above, I'm showing an example of a “problematic” pattern, with an impure reducer… but everything seems to work fine! The clock is showing the correct time, even before our refactor.

In truth, impure reducers will work fine in most situations, but there are some edge-cases that can cause problems. We'll talk about this more in the next module, when we cover concurrency in React.

Even ignoring those edge-cases, though, I think it makes sense to do any impure work outside of our reducers. Reducers are where all of the complexity lives, in terms of state changes, and we want them to be as simple and predictable as possible. Keeping them pure helps with that, and it means that they're easier to write unit tests for!

Finally, the React team expects us to write pure reducers. They make a big deal about this in the official docs. If we want to avoid mysterious bugs slipping into our code in future versions of React, we better keep them pure!

## Quick example

```jsx
import React from 'react';

const INITIAL_STATE = {
  colors: [
    '#FFD500',
    '#FF0040',
    '#FF0040',
    '#FF0040',
    '#FF0040',
  ],
  numOfVisibleColors: 2,
};

function reducer(state, action) {
  switch (action.type) {
    case 'add-color': {
      return {
        ...state,
        numOfVisibleColors:
          state.numOfVisibleColors + 1,
      };
    }

    case 'remove-color': {
      return {
        ...state,
        numOfVisibleColors:
          state.numOfVisibleColors - 1,
      };
    }

    case 'change-color': {
      const nextColors = [...state.colors];
      nextColors[action.index] = action.value;

      return {
        ...state,
        colors: nextColors,
      };
    }
  }
}

function App() {
  const [state, dispatch] = React.useReducer(
    reducer,
    INITIAL_STATE
  );
  const { colors, numOfVisibleColors } = state;

  const visibleColors = colors.slice(
    0,
    numOfVisibleColors
  );

  const colorStops = visibleColors.join(', ');
  const backgroundImage = `linear-gradient(${colorStops})`;

  function addColor() {
    if (numOfVisibleColors >= 5) {
      window.alert(
        'There is a maximum of 5 colors'
      );
      return;
    }

    dispatch({ type: 'add-color' });
  }

  function removeColor() {
    if (numOfVisibleColors <= 2) {
      window.alert(
        'There is a minimum of 2 colors'
      );
      return;
    }

    dispatch({ type: 'remove-color' });
  }

  return (
    <div className="wrapper">
      <div className="actions">
        <button onClick={removeColor}>
          Remove color
        </button>
        <button onClick={addColor}>
          Add color
        </button>
      </div>

      <div
        className="gradient-preview"
        style={{
          backgroundImage,
        }}
      />

      <div className="colors">
        {visibleColors.map((color, index) => {
          const colorId = `color-${index}`;
          return (
            <div
              key={colorId}
              className="color-wrapper"
            >
              <label htmlFor={colorId}>
                Color {index + 1}:
              </label>
              <div className="input-wrapper">
                <input
                  id={colorId}
                  type="color"
                  value={color}
                  onChange={(event) => {
                    dispatch({
                      type: 'change-color',
                      value: event.target.value,
                      index,
                    });
                  }}
                />
              </div>
            </div>
          );
        })}
      </div>
    </div>
  );
}

export default App;
```


```jsx
import React from 'react';
import produce from 'immer';

const SIZES = [
  { slug: 'sm', label: 'Small (10")' },
  { slug: 'md', label: 'Medium (12")' },
  { slug: 'lg', label: 'Large (14")' },
  { slug: 'xl', label: 'Pizza For Days (16")' },
];
const TOPPINGS = [
  { slug: 'anchovies', label: 'Anchovies' },
  { slug: 'mushrooms', label: 'Mushrooms' },
  { slug: 'green-pepper', label: 'Green Pepper' },
  { slug: 'onions', label: 'Onions' },
  { slug: 'pineapple', label: 'Pineapple' },
  { slug: 'pepperoni', label: 'Pepperoni' },
  { slug: 'sausage', label: 'Sausage' },
  { slug: 'chicken', label: 'Chicken' },
  { slug: 'bacon', label: 'Bacon' },
  { slug: 'feta', label: 'Feta' },
  { slug: 'provologne', label: 'Provolone' },
  { slug: 'gummy-bears', label: 'Gummy Bears' },
  { slug: 'popcorn', label: 'Popcorn' },
  { slug: 'lucky-charms', label: 'Lucky Charms' },
  {
    slug: 'ice-cream',
    label: 'Vanilla Ice Cream',
  },
  { slug: 'cotton-candy', label: 'Cotton Candy' },
];

const INITIAL_STATE = {
  size: undefined,
  toppings: {},
};

function reducer(state, action) {
  return produce(state, (draftState) => {
    switch (action.type) {
      case 'change-size': {
        draftState.size = action.slug;
        break;
      }
      case 'add-topping': {
        draftState.toppings[action.slug] = true;
        break;
      }
      case 'remove-topping': {
        delete draftState.toppings[action.slug];
        break;
      }
      case 'add-all-toppings': {
        action.slugs.forEach((slug) => {
          draftState.toppings[slug] = true;
        });
        break;
      }
      case 'remove-all-toppings': {
        draftState.toppings = {};
        break;
      }
    }
  });
}

function OrderPizza() {
  const [state, dispatch] = React.useReducer(
    reducer,
    INITIAL_STATE
  );
  const id = React.useId();

  const hasSelectedAllToppings = TOPPINGS.every(
    ({ slug }) => state.toppings[slug] === true
  );

  function handleSubmit(event) {
    event.preventDefault();

    // TODO: call window.alert() with the selected toppings.
    window.alert(JSON.stringify(state, null, 2));
  }

  function handleToggleToppings() {
    console.log(hasSelectedAllToppings);
    if (hasSelectedAllToppings) {
      dispatch({
        type: 'remove-all-toppings',
      });
    } else {
      dispatch({
        type: 'add-all-toppings',
        slugs: TOPPINGS.map((topping) => topping.slug),
      });
    }
  }

  return (
    <form onSubmit={handleSubmit}>
      <h2>Your order</h2>
      <fieldset>
        <legend>Select size:</legend>
        <div className="size">
          {SIZES.map(({ slug, label }) => {
            const inputId = `size-${slug}`;

            return (
              <label key={inputId} htmlFor={inputId}>
                <input
                  id={inputId}
                  type="radio"
                  name={`${id}-size-group`}
                  value={slug}
                  checked={slug === state.size}
                  onChange={() =>
                    dispatch({
                      type: 'change-size',
                      slug,
                    })
                  }
                />
                {label}
              </label>
            );
          })}
        </div>
      </fieldset>

      <fieldset>
        <legend>Select your pizza toppings:</legend>
        <div className="toppings">
          {TOPPINGS.map(({ slug, label }) => {
            const inputId = `topping-${id}-${slug}`;
            const hasTopping =
              state.toppings[slug] === true;

            return (
              <label key={inputId} htmlFor={inputId}>
                <input
                  id={inputId}
                  type="checkbox"
                  checked={hasTopping}
                  onChange={() => {
                    dispatch({
                      type: hasTopping
                        ? 'remove-topping'
                        : 'add-topping',
                      slug,
                    });
                  }}
                />
                {label}
              </label>
            );
          })}
        </div>
        <div className="topping-actions">
          <button
            onClick={handleToggleToppings}
            type="button"
          >
            {hasSelectedAllToppings
              ? 'Remove All'
              : 'Select All'}
          </button>
        </div>
      </fieldset>

      <div className="actions">
        <button>Order pizza</button>
      </div>
    </form>
  );
}

export default OrderPizza;
```