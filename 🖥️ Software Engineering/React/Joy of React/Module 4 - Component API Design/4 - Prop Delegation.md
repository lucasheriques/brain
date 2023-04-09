When working with those primitive UI components, that might mean that you have to foward maybe 10 props to the primitive component.

Instead of listing them out one by one, use the `{...spread}` syntax.

# Conflicts

Depending on where you put the `{...delegated}` props, it might override other default props.

If you have a `Checkbox` component, but the user consumer does something like:

```js
<Checkbox
	type="button
/>
```

The consumer has "hacked" our component - it's now a button, and not a checkbox.

As the producer, you have the power to determine how much power/flexibility should go to the consumers of your component.

TLDR:

1. If we want to allow the consumer to overwrite a particular hardcoded attribute, we can place the `{...delegated}` syntax afterwards.
2. If we want to prioritize the hardcoded attribute, the `{...delegated}` should come first.
3. If we want to merge both values, we'll need to manage it ourselves, without using `{...delegated}`.

All three options are valid strategies, which can depend on your use case.

# Delegating Styles

If you're buiding a low-level component, like a Button, Slider, DatePicker, etc, we often want to make sure the consumer can apply custom styles. A component like this might be used a lot in the application, so it makes sense to provide this flexibiliity.

There's two options to do that:

1. Granular props, like `textColor`, `fontWeight`, etc
2. Supplying a custom `className`, which will apply the styles based on the value

### Arguments for specific props

When building low-level components, we're likely implementing them according to a design system. So, we often want to make sure developers use colors from that system.

If we expose a className prop, a rogue developer coudl radically change how this component is styled.

A professional-looking app is one that is consistent, where each Slider instance is a part of a visual set. With the `className` prop, the app will eventually lose that consistency.

Components are meant to encapsulate markup, logic and *styles*. If the developers can apply any styles they want, then we don't truly have encapsulation.

## Arguments for `className` prop

CSS is a huge, sprawling language. We could wind up with 50+ props, which would be a nightmare to maintain, and no fun at all to consume. Also, designers might create an exception and one-offs, so it won't be long until there is a legitimate use case that does not work with the specific props.

It's just not realistic to come up with a handful of style-related props that will work for every possible use case.

### Josh's take

Add a `className` prop. Polish and UX is more important than consistency. Developers usually will not bend the component into an unrecognizable shape. Designers are the one that might do a couple of tweaks, to create the best possible UX. It's usually something small that still fits within the *spirit* of the design system.