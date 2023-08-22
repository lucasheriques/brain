To talk about memoization, `useCallback` and `useMemo`, we need to be really comfortable with the React render cycle. Let's refine on our concepts.

### Basic rule

**Every re-render in React starts with a state change**. It is the only trigger in React for a component to re-render.

**Re-renders only affect the component that owns the state + any descendants (if any).**

React's main job is to keep the app UI in sync with the React state. The point of a re-render is to figure out what needs to change.

Each render is like a snapshot, a photo that tells us what the UI *should* look like, based on the current application state.

After this, React plays a game of "finding the differences" to figure out what changed between snapshots (called **reconciliation**). After this process is done, React settles back and waits for the next state change. This is what we call **[[2.1 - Core React Loop]]**.

The point of a re-render is to figure out how a state change should affect the UI. So we need to re-render all potentially-affected components, in order to get an accurate snapshot.

**Props have nothing to do with re-renders.** So, even if a component doesn't have a prop that uses a state variable, if his parent component re-renders, the same thing is going to happen to all child components, regardless of their props. This can be wasteful at times, but there are ways to optimize.

[[8.1 - React.memo (Pure Components)]]