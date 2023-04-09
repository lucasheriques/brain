We write tests to be confident that our application will work when the user uses them. Some people write tests to enhance their workflow as well and that's great, but I'm ultimately interested in confidence. That being the case, what we test should map directly to enhancing our confidence. Here's the key point I want you to consider when writing tests:

> Think less about the code you are testing and more about the use cases that code supports. The more your tests resemble the way your software is used, the more confidence they can give you.


## [Code Coverage < Use Case Coverage](https://kentcdodds.com/blog/how-to-know-what-to-test#code-coverage--use-case-coverage)

So the coverage report helps us identify what code in our codebase is missing tests. So when you look at a code coverage report and note the lines that are missing tests, don't think about the ifs/elses, loops, or lifecycles. Instead ask yourself:

> What use cases are these lines of code supporting, and what tests can I add to support those use cases?

Key takeaway:

**Test use cases, not code.**

## About React

When writing code, remember that you already have two users that you need to support: End users, and developer users. Again, if you think about the code rather than the use cases, it becomes dangerously natural to start testing implementation details. When you do that, your code now has a third user.


Here are a few aspects of React that people often think about testing which results in implementation details tests. For all of these, rather than thinking about the code, think about the observable effect that code has for the end user and developer user, that's your use case, test that.

-   Lifecycle methods
-   Element event handlers
-   Internal Component State

Conversely, here are things that you should be testing because they concern your two users. Each of these could change the DOM, make HTTP requests, call a callback prop, or perform any other number of _observable_ side effects which would be useful to test:

-   User interactions (using [`userEvent`](https://testing-library.com/docs/ecosystem-user-event) from `@testing-library/user-event`): Is the end user able to interact with the elements that the component renders?
-   Changing props (using [`rerender`](https://testing-library.com/docs/react-testing-library/api#rerender) from React Testing Library): What happens when the developer user re-renders your component with new props?
-   Context changes (using [`rerender`](https://testing-library.com/docs/react-testing-library/api#rerender) from React Testing Library): What happens when the developer user changes context resulting in your component re-rendering?
-   Subscription changes: What happens when an event emitter the component subscribes to changes? (Like firebase, a redux store, a router, a media query, or browser-based subscriptions like online status)

## How to know where yo start?

So here's what you do, consider your app from the user's point of view and ask:

> What part of this app would make me most upset if it were broken?

Alternatively, and more generally:

> What would be the worst thing to break in this app?


Once you have that prioritized list, then I suggest writing a single end to end (E2E) test to cover the "happy path" that most of your users go through for the particular use case. Often you can cover parts of several of the top features on your list this way. This may take a little while to get set up, but it'll give you a HUGE bang for your buck.


Once you have a few E2E tests in place, then you can start looking at writing some integration tests for some of the edge cases that you are missing in your E2E tests and unit tests for the more complex business logic that those features are using. From here it just becomes a matter of adding tests over time. Just don't bother with targeting a 100% code coverage report, it's not worth the time.