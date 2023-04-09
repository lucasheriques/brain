Instead of trying to encapsulate all the possible settings in different props, we can add an specific prop for the user to include whatever markup he wants. Here's how it looks:

```jsx
function CaptionedImage({ image, caption }) {
  return (
    <figure>
      {image}
      <div className="divider" />
      <figcaption>{caption}</figcaption>
    </figure>
  );
}

// We'd use it like this:

<CaptionedImage
  image={
    <img
      alt="A punk-rock cat illustration"
      src="https://sandpack-bundler.vercel.app/img/punk-cat.png"
    />
  }
  caption="Illustration by Josh Comeau"
/>
```

In this case, essentially, we're saying the `image` prop takes a *React element*. Kinda like we do with the `children` prop.

The nice thing about this pattern is that we can include *multiple slots* in a single component. Kinda like being able to specify multiple distinct children.

This pattern provides **maximum control and power to the consumer**:
- With [[4 - Prop Delegation]], we're able to provide additional props to a particular element.
- With [[6 - Polymorphism]], we're able to change a particular element's HTML tag.
- With slots, we're able to provide any markup we want, without restrictions.

This is not necessarily a good thing. It's a tradeoff. The more power we give to the consumer, the more flexible our component is, but the more likely it is for things to go awry.

### Passing components are props

Remember that components are just functions. So, the same way we can pass a state setter, we can also pass a component.

Then, it's up to the descendant on how to render that component.

```jsx
// App.js
import React from 'react';
import {
  Award,
  Camera,
  Frown,
  Slash,
  XCircle,
} from 'react-feather';

import IconButton from './IconButton';

function App() {
  return (
    <>
      <IconButton icon={Award}>
        Collect Award
      </IconButton>
      <IconButton icon={Frown}>
        Rate Our Product
      </IconButton>
      <IconButton icon={XCircle}>
        Dismiss
      </IconButton>
    </>
  );
}

export default App;

// IconButton.js
import React from 'react';

import styles from './IconButton.module.css';

function IconButton({ icon: Icon, children }) {
  return (
    <button className={styles.wrapper}>
      <span className={styles.iconWrapper}>
        <Icon size={20} strokeWidth={1.5} />
      </span>
      <span className={styles.childrenWrapper}>
        {children}
      </span>
    </button>
  );
}

export default IconButton;
```

