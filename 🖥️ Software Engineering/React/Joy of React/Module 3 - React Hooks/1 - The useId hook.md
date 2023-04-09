One of the core ideas of React is reusable. React is a library built with components in mind, and we should be able to render just about any kind of component without anything blowing up.

Certain aspects of the web platform aren't built with reusability in mind. For example, the `id` attributes needs to be globally unique. How can we create reusable components without accidentally violating this rule?

We could add a prop to the component, like `id`. Then, the engineer can specify a unique value for each instance.

This works, however, it relies on the engineer to remember supplying a value, and making sure it's unique, which is a hard task by itself.

However, now we have access to a new tool: the `React.useId` hook. For each instance of the component, it'll get a different value. So, for instance, if we render two components, the first one will have the `id` equal to `:r0:` and second one will have `:r1:`.

React **hooks into** the component instance, so this ID lives on the instance and will not change between re-renders.

Another benefit: the `useId` hook produces the same value across server and client renders.