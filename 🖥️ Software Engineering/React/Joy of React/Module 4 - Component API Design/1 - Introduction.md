Often, when creating a new React application as a solo developer, you're both the **producer** of the components and their **consumer** as well.

What that means is that each component will be built by you, for your own use.

However, in a larger team, that is not the case. Maybe you'll build a custom `Modal` component, because you're on the components team, but this `Modal` will be used by the Onboarding team, which will use your `Modal` to do something fancy.

The way other people (and yourself) interact with your component is defined by its `props`. You, as the producer, controls what the props do, which ones are included, and this is a tremendous power. You can think of the `props` as the interface they interact with your API.

If we do a nice job on this interface – if the props are intuitive and nice to use – then it'll be lovely to use.

It also has to do with consistency. Do the components always follow the same patterns?

This is often the difference between a React application that feels maintainable vs one that doesn't. 

The consumer experience is often much more important than the producer experience, and so we should be really intentional about the way we set up the props for our components.