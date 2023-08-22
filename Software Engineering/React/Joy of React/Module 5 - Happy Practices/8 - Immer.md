Immer is an [NPM package](https://www.npmjs.com/package/immer) built by Michel Weststrate (creator of MobX). Michel was frustrated by how tricky immutable updates could be, and so he created a tool to make it more manageable.

Here's what Immer does in a nutshell: it allows us to write code that _looks_ like it mutates the data. Using some modern JS trickery, however, the data is never actually mutated.

## A working draft

The `produce` function we get from Immer takes two arguments:

-   The state we'd like to edit (`currentState`)
-   A callback function (`(draftState) => {}`)

`draftState` is a special “wrapped” version of `currentState`. I like to think of it as a shielded version: Immer is its guardian, and will make sure that the original object is never mutated, no matter _what_ we try to do to this wrapped version.

After running the code in our callback function, `produce` will resolve to a brand-new object, with all of the modifications applied. Example:

```jsx
import React from 'react';
import produce from 'immer';

function App() {
  const [numbers, setNumbers] = React.useState([0, 1, 2]);
  
  function handleClick() {
    const nextState = produce(numbers, (draftState) => {
      const nextNumber = numbers.length;
      draftState.push(nextNumber);
    });
    
    setNumbers(nextState);
  }
  
  return (
    <>
      <h2>Data contents:</h2>
      <div className="items">
        {JSON.stringify(numbers)}
      </div>
      
      <div className="actions">
        <button onClick={handleClick}>
          Add next number
        </button>
      </div>
    </>
  );
}

export default App;
```

## Drawbacks

No tool is perfect, and every NPM package will have some trade-offs.

The biggest issue is that proxies can't easily be logged. Trying to `console.log` produces some pretty inscrutable results.

**Here's the good news:** Immer ships with a tool, `current`, which can help "unpack" a proxy, for debugging purposes:

```js
import produce, { current } from 'immer';

const arr = [1, 2, 3];
produce(arr, (draftArr) => {
  draftArr.push(4);

  console.log(current(draftArr));
  // [1, 2, 3, 4]
});
```

To be clear, you shouldn't ever need to use `current` in your final production code. It's a tool that exists purely to help you debug, while you're solving the problem at hand.

It can be a bit annoying to need to import and apply a function just to see what the current value is, but in my opinion, it's a small price to pay.