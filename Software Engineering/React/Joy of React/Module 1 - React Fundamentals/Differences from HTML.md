# Reserved words

Remember that JSX compiles down to JavaScript, and not HTML. There are some words that are used in HTML, but they're also used in JS, which is why those words are invalid in JSX.

Examples:
- for -> htmlFor
- class -> className

# Self-closing tags

The JSX compiler isn't as flexible as HTML.

```html
<div>
	<p>This paragraph is opened… but never closed.
	<p>We're omitting the closing tags!
</div>
```

This is valid HTML, because the browser understands that a `<p>` can't start before the end of the other paragraph. JSX won't accept this, however.

In JSX, we always need to self-close all tags - including element's that don't have closing tags in HTML, like `<input>` and `<image>`.

# Case-sensitive tags

HTML is case-insensitive, JSX is case-sensitive. All tags must be lower case, because if it's uppercase it's how JSX handle custom components.

# Case-sensitive attributes

Attributes in JSX need to be `camelCase`, examples:

- `autoplay` -> `autoPlay`
- `onclick` -> `onClick`
- tabindex -> `tabIndex`
- `stroke-dasharray` -> `strokeDasharray` (SVGs)

**Exceptions: Data and ARIA attributes**

# Inline styles

In JSX, `style` takes an object, and all CSS properties are written in camelCase.

-   `background-position` becomes `backgroundPosition`
-   `border-bottom-color` becomes `borderBottomColor` 
-   `-webkit-font-smoothing` becomes `WebkitFontSmoothing`

In React, it's common convention to use unitless values where possible, but you can also use full units.