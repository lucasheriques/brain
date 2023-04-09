Two main reasons for memoizing something:
1. Improve performance by avoiding expensive computations, like re-rendering extensive components or calling expensive functions (think caching)
2. Value stability


So when _should_ I `useMemo` and `useCallback`?

PS:

> `useMemo` is similar to `useCallback` except it allows you to apply memoization to any value type (not just functions). It does this by accepting a function which returns the value and then that function is _only_ called when the value needs to be retrieved (which typically will only happen once each time an element in the dependencies array changes between renders).

`useCallback` allows you to apply memoization to functions. It returns a _memoized_ callback. That callback is only called if the dependency list changes.

`useMemo` on the other hand allows you to apply memoization to any value. It returns a _memoized_ value. It'll only recompute that values if the any of the dependencies have changed.


There are specific reasons both of these hooks are built-into React:

## Referential equality

```js
true === true // true
false === false // true
1 === 1 // true
'a' === 'a' // true

{} === {} // false
[] === [] // false
() => {} === () => {} // false

const z = {}
z === z // true

// NOTE: React actually uses Object.is, but it's very similar to ===
```

Because of how JavaScript works, every time we define a new object/array/function, they're not going to be the referentially equal to the last time the same object was defined (even if they have the same properties and values).

That's where `useMemo` and `useCallback` come in.  There's two situations where referencial equality matters in React:

### [Dependencies lists](https://kentcdodds.com/blog/usememo-and-usecallback#dependencies-lists)

When the values of the dependencies lists (`useEffect`, `useLayoutEffect`, `useCallback`, and `useMemo`) are objects instead of primitive values. We use them to avoid re-renders.

### [`React.memo` (and friends)](https://kentcdodds.com/blog/usememo-and-usecallback#reactmemo-and-friends)

> **MOST OF THE TIME YOU SHOULD NOT BOTHER OPTIMIZING UNNECESSARY RERENDERS.** React is VERY fast and there are so many things I can think of for you to do with your time that would be better than optimizing things like this. In fact, the need to optimize stuff with what I'm about to show you is so rare that I've literally _never_ needed to do it in the 3 years I worked on PayPal products and the even longer time that I've been working with React.

If we have a value (that can be an object, or even a React Component) we can wrap it in `useMemo` so it will only re-render if the dependency list changes. A use case might be if we have a expensive component (highly interactive Graph/Charts/Animations).

> I would like to re-iterate that I strongly advise against using `React.memo` (or it's friends `PureComponent` and `shouldComponentUpdate`) without measuring because those optimizations come with a cost and you need to make sure you know what that cost will be as well as the associated benefit so you can determine whether it will actually be helpful (and not harmful) in your case, and as we observe above **it can be tricky to get right all the time so you may not be reaping any benefits at all anyway.**


## Computationally expensive calculations

This one is about `useMemo`, because it doesn't apply to `useCallback`.


## `useCallback` use cases

The purpose of `useCallback` is to memoize a callback for use in dependency lists and props on memoized components. The _only_ time it’s useful to use `useCallback` is when the function you’re memoizing is used in one of those two situations.