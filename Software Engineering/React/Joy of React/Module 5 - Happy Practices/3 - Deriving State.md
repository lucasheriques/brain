Based on [this lesson](https://courses.joshwcomeau.com/joy-of-react/05-happy-practices/03-deriving-state).

One of the established "Best Practices" is to always store the minimum amount of data in state. If something can be derived from state, it should.

But, what does that mean?

When adding new features to an application, if the state is simpler, it is much easier to maintain and to change the code - because the state is in a simple shape (like a primitive value, or an array of primitive values).

By storing the minimum amount of data in state, we keep that state easier to conceptualize. There's something really elegant about the state being a “pure” representation of the data.

Over time, apps tend to grow more and more complex, as we add more and more features. If we had 10 state variables in the Game component, wouldn't it be nicer if they were easier to reason about?

This also applies when it comes to **state updates.**

There are exceptions (which we'll talk about shortly), but as a general rule, our life becomes much easier when we don't store derived data in state.

However, maybe the rerunning these calculations on every render might be expensive. Instead of storing it on state, just memoize the component, like we learned before on [[8.1 - React.memo (Pure Components)]].

# Breaking the Rules

The golden rule we've been following is that if something can be derived from state, it should be derived from state.

However, it's ok to break rules sometimes, as long as you're doing it intentionally, and with confidence.

There are no real "best practices". Deriving state is a good idea 95% of the time, but there are always going to be excpetions.

