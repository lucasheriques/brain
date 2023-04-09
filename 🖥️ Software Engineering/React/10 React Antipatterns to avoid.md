# Big Components
Antipattern:  deeply nested component. It's hard to understand, refactor and test.

We can improve it by extracting it into reusable components.

This VS Code extension, Glean, helps with that.

However, avoid over-optimization too. Start writing a big component, then break it down.

# Nesting Components
Don't define new child components within the parent. If you do that, every time the Parent component is rendered, it is going to redefine the Child component as well, which can lead to performance issues.

How to solve: don't define the child component at all, or define it in a new component.

# Failure to Memoize
If you have a component with an expensive calculation and multiple state fields, every time one state field changes, it'll redo the calculation. If this calculation only depends on specific fields, memoize it using `useMemo` to avoid having to re-calculate this value.

This might also happen with functions, which then you can use the `useCallback` hook.

# Useless Divs

JSX must return one single element (that may contain childs). Because of that, you might add a couple of `<div>`s to encapsulate the return. However, this can causes issues with CSS styling and accessibility.

Instead, use `<React.Fragment>`, or, its shorthand version, `<>`.

# Messy Files

As your app grows, you'll create more and more components. You want an opinionated way to organize them. A good rule to follow is one component per file.

In larger projects, you can take this one step further and define one component per folder. This allows you to use a `index.tsx` file for it, and add relevant files such as `.spec`, `.stories`, `.css` files inside the folder.

# Big Bundles

When you ship your app with big JS bundle to prod, it'll have a big initial loading time, because it takes some time to the browser to download the JS. What can we do?

If you use something like CRA or Next, it uses Webpack, which means it's easy to implement code splitting. It allows you to split the imports so the JS only gets imported once it's needed. However, this only works for plain JS. For React, you can use `React.lazy`, however that is still experimental.

# Prop Drilling

If you have a component that has to pass the same prop too far down the tree, that is called prop drilling. You don't actually need the prop, only to pass it along to a deeper child.

One solution is to bring a global state management approach like Redux, but it can be too much.

An easier solution is the Context API, which allows you to consume it usin the `useContext` hook. However, that should be more like a dependency injection system, since every time the context changes, all components within it should be re-rendered. Also, it makes your component impossible to reuse without having that provider as a parent.

Most apps have a few values that you want to be global, but everything else should be more localized. 

# Prop Plowing

If you have too many props to pass within an object, you can use the spread operator `{...object}` to avoid having to pass many props down. However, do not overuse it, since it does makes your code less clear.

# Messy Events

When you have a function that takes the event as the first arguments, but one or more values as the second argument, that means when you call it, you'll have to break out an arrow function that can be confusing if you need it in multiple places.

```ts
function App() {
	const handleIt = (e: any, v: number) => {
		console.log(e, v);
	}

	return (
		<>
			<input onChange={(e) => handleIt(e, 1)} />
			<input onChange={(e) => handleIt(e, 2)} />
			<input onChange={(e) => handleIt(e, 3)} />
		</>
	)
}
```

A cool JS trick you can use is to create a curried function. Which is just a function that returns another function.

```ts
function App() {
	const handleIt = (v: number) => {
		return (e: any) => console.log(e, v);
	}

	return (
		<>
			<input onChange={(e) => handleIt(1)} />
			<input onChange={(e) => handleIt(2)} />
			<input onChange={(e) => handleIt(3)} />
		</>
	)
}
```

The outer function takes our custom arguments, while the inner function handles the event that is passed by default. This eliminates the need of defining an arrow function, which makes your code look a lot cleaner.

# Coupled State

When working with the `useState` hook in the component, it's tempting to put all of your data in a single object. Makes your code look cleaner, and may look more performant, because you only need to call `setState` once.

```ts
function Feature() {
	const [state, setState] = useState({
		count: 0,
		x: 100,
		y: -10,
		title: 'yo',
		name: 'Lucas',
		time: new Date()
	})
}
```

However, you should know that React 18 will do automatic batching whenever you update the state. That means that calling `setState` multiple times in the same function will not trigger multiple re-renders. Therefore it's not a big deal for performance. But, more importantly, it makes your code harder to extract into a custom hook.

In the old Class components days, it was common to organize the code into Smart and Dumb components. Smart components controlled the data, and Dumb components displayed the UI.

Nowadays, it's easier to extract your logic into a custom hook. A good approach is starting to build the component with multiple stateful values at first, then if it gets too complex, or you want to use into a different component, you extract it into a new custom hook. Which is itself just a JS function. This allows us to treat all your components as Dumbs component, and your custom hooks handle the complex business logic.