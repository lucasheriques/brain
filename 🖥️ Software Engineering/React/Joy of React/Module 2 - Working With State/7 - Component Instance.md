TLDR: When React render a component, each one of them gets a component instance as well. Instance holds the state of the component.

When we render a component, we "mount" it. Mounting involves two steps:

1. Evaluating the JSX and pass it into React, so React create the DOM elements
2. Creating the *component instance*, a long-lived object that holds contextual information about this particular instance of the component

State is stored within this instance. When we write `React.useState`, the code "hooks" into the instance.
When the component is **unmounted** (for example, with conditional rendering), we destroy that instance, hence, all state is lost.

Component instances allow us to render multiple "copies" of the same component, with each one having its own internal state.