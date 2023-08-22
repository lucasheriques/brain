---
tags: react, web
---
Events occur when the user interacts with the browser, like:
- clicking a button
- moving their cursor

in order to respond to an event, we need to listen for it. In pure JS, that would be:

```js
const button = document.querySelector('.btn');

function doSomething() {
	// do things
}

button.addEventListener('click', doSomething);
```

the web platform also allows another way to do this:

```html
<button class="btn" onclick="doSomething()">
	Click me!
</button>
```

React follows this convention, being similar to it:

```jsx
function App() {
	function doSomething() {
		// stuff
	}
	return (
		<button onClick={doSomething}>
			Click me!
		</button>
	)
}
```

this is how we should do it in React, instead of interactign with the DOM directly. Reasons:

1. **Automatic cleanup** - no need to call `removeEventListener`, since React does that for us automatically
2. **Improved performance**: React can optimize things, like batching multiple event listeners together to reduce memory consumption
3. **No DOM interaction**: React likes for us to stay within its abstraction, due to its implementation of how to parse DOM changes (mainly the VDOM)

## Passing a function reference

When adding a event handler in React, we pass a reference to a function, not the function call itself (like we do in HTML).

```html
// ✅ We want to do this:
<button onClick={doSomething} />

// 🚫 Not this:
<button onClick={doSomething()} />

```

when we call the function, that means that it's gonna be called as soon as the app is rendered. We do not want that, since we want to call the function once the event is triggered. So, we pass a reference to that function so React can call it in a later time.

```js
// ✅ Correct.
// Will be called when the user clicks the button.

React.createElement(
	'button',
	{
		onClick: doSomething,
	}
);

// 🚫 Incorrect
// Will be called immediately, when the element is created.
React.createElement(
	'button',
	{
		onClick: doSomething(),
	}
);
```