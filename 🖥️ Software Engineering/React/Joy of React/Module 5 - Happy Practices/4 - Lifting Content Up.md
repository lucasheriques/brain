Lifting content up is when you move an element up in the tree, so it it's owned by another element.

We create a **slot** for adding arbitrary React elements. See more in [[8 - Slots]].

When creating this slot, now the parent element has the freedom to pass whatever content he wants.

When thinking about components, we're constantly thinking in terms of *parent* and *children*. That's how we think about DOM nodes. But, when talking about React, there's another concept: **owners** and **ownees**.

We can see this terms all over the place on the [React codebase](https://github.com/facebook/react/search?q=owner).

When a React element is created within a component, we say that component "owns" that element. It decides what the props should be.

So, when restructuring using this pattern, it doesn't really change the parent/child relationship, but it does change which component owns the other which was lifted up. By lifting the element up, we're changing which component is responsible for setting its props.


# Tools to create usable components

We have lots of different tools that we can use to provide an amazing experience to the consumer of our components. 

- Lifting Content Up
- Wether to prop drill or not
- [[1 - Leveraging Keys]]

It all comes down to each context that we're using them.

The trick is to get comfortable using the right tool in the right circumstance. That's why it's better to understand the reasoning regarding "best practices", so you can use your intuition instead of a hard rule.