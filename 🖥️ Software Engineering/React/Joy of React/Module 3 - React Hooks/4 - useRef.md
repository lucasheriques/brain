When we're writing JSX, we're not writing HTML. JSX is the React idiomatic way to write HTML, which is great because it does come with great abstractions.

However, sometimes we do need to work with the actual DOM element. Now, we could do that with `document.querySelector`, however, we do not want to go around the React abstraction.

The way to solve that is using the `ref` attribute. 

```js
<canvas
  width={200}
  height={200}
  ref={function (canvas) {
    console.log(canvas); // <canvas> DOM node
  }}
/>
```

When React renders this component, it'll invoke the `ref` function and provide the underlying DOM node. However, this is expensive, as it'll run on every render.

The better way to solve this is to do this only once, when the component renders. Then, we just pass the canvas reference on subsequente rerenders.

The way to to that is by using the `useRef` hook. When we use it, we receive an object with a `current` property. If we pass an object with this shape to the `ref` attribute, React will mutate this object, setting `current` to be equal the `canvas` reference.

This only runs when the component first renders, leading to improved performance.

### Other use cases
Capturing a DOM node is the most common useCase, but `useRef` can be used for other things as well.

`useRef` is a box, and we can put anything we want there (strings, numbers, objects, arrays, etc). We'll see more examples later.