When choosing an HTML tag, **it's much more important to focus on the semantics than the aesthetics**. You should use a a `<buton>` even if you don't want it to look like a button. With CSS, we can strip away all of those built-in button styles. It's much easier to remove a handful of CSS rules than it is to create all the usability benefits built into the `<button>` tag.

Some ideas on how to implement this:

```jsx
// List.js
import React from 'react';

import styles from './List.module.css';

const VALID_TAGS = ['ul', 'ol'];

function List({
  // ol | ul
  as: Tag = 'ul',
  className = '',
  children,
  ...delegated
}) {
  if (!VALID_TAGS.includes(Tag)) {
    throw new Error(
      `Unrecognized tag: ${Tag}. Expected: ${VALID_TAGS}`
    );
  }

  return (
    <Tag
      {...delegated}
      className={`${styles.wrapper}`}
    >
      {children}
    </Tag>
  );
}

export default List;


// App.js
import React from 'react';

import List from './List'

function App() {
  return (
    <main>
      <List>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
      </List>
      <List as="ol">
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
      </List>
    </main>
  );
}

export default App;


// SectionWithHeading.js
import React from 'react';

function SectionWithHeading({
  level,
  title,
  children,
}) {
  if (
    typeof level !== 'number' ||
    level < 1 ||
    level > 6
  ) {
    throw new Error(
      `Unrecognized heading level: ${level}`
    );
  }

  const HeadingTag = `h${level}`;

  return (
    <section>
      <HeadingTag>{title}</HeadingTag>
      {children}
    </section>
  );
}

export default SectionWithHeading;
```


