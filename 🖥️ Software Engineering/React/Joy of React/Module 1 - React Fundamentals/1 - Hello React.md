How does React works under the hood?

```js
const element = React.createElement(
  'p',
  { id: 'hello' },
  'Hello World!'
);
```

`React.createElement` is a function that accepts 3 or more arguments:

1.  The type of the element to create.    
2.  The properties we want this element to have.
3.  The element's contents, what the element should have as children.

This function returns a “React element”. React elements are plain old JavaScript objects. If we inspect it with `console.log(element)`, we'll see something like this:

```js
{
  type: "p",
  key: null,
  ref: null,
  props: {
    id: 'hello',
    children: 'Hello World!',
  },
  _owner: null,
  _store: { validated: false }
}
```

This JavaScript object is a _description_ of a hypothetical paragraph tag, with an ID of `hello`, containing the text `"Hello World!"`. This information will be used to construct the _actual_ paragraph we can see in-browser.

Later in this course, we'll learn about `key` and `ref`. The final two properties, `_owner` and `_store`, are meant to be used internally by React, and can be safely ignored by us.

The object returned by `createElement` is a JS object that describes the element we want to render.