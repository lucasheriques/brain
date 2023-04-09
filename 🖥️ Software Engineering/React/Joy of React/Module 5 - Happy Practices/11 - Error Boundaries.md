We can add error handling to our applications, but it's too hard to anticipate all possible errors. Almost by definition, errors are rare events, edge cases that are hard to predict.

Errors Boundaries allow us to quarantine errors events based on the component that they wrap.

By wrapping up a component in a `<ErrorBoundary>`, if an error happens, we can show a custom fallback message (or nothing).

```jsx
import React from 'react';

class ErrorBoundary extends React.Component {
  // Equivalent to:
  // const [hasError, setHasError] = useState(false);
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    console.error(error);
    console.info({ errorInfo });
  }

  render() {
    if (this.state.hasError) {
      return this.props.fallback || null;
    }

    return this.props.children;
  }
}

export default ErrorBoundary;

```

Unfortunately, error boundaries are one of the features that have not been migrated to hooks, which means we need to use class components. Here's a quick summary of the code:

-   `constructor` is used to initialize state variables.
-   `render` is where all of the render stuff goes. This method is equivalent to everything inside our functional component _except_ the hooks.
-   `componentDidCatch` allows us to log when errors happen
-   `getDerivedStateFromError` implements the error boundary.

When an error happens within any descendant component, the `getDerivedStateFromError` method intercepts it. Instead of blowing up the whole page, it flips our state variable, `hasError`, from false to true.

In the render method, we render the `children` prop by default (the `<Ticker>` element), but if `hasError` is true, we render the fallback content instead, if provided.

This handy component can be used to "wall off" different sections of our application, guaranteeing that problems in one section don't affect the other. As a result, small problems in our code don't cause _big_ problems for our users!

## Error tracking

Error boundaries allow us to soften the blow of an unexpected code failure, but what if we wanted to be notified about them, so that we can fix the problem altogether for future users?

Error trackers like [Sentry](https://sentry.io/) and [LogRocket](https://logrocket.com/) can help us catalog these unexpected issues. They'll let us see how often the issues are occurring, and provide a bunch of metadata to help us understand and fix the problem.

The Sentry SDK even has an [ErrorBoundary component](https://docs.sentry.io/platforms/javascript/guides/react/features/error-boundary/). It's quite a bit like the one we saw in this lesson, but it also collects data about the failure for us.

Error tracking is beyond the scope of this course, but feel free to dig into this if you're interested in this topic!