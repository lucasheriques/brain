To forward refs on functional components, we use the HOC `React.forwardRef`. It allow us to get the `ref` from the component and attach to whatever element we think it's best. Keep in mind the `ref` will not be passed in the `props` object.

```js
import React from 'react';

import styles from './Slider.module.css';

function Slider(
  { label, ...delegated },
  ref
) {
  const id = React.useId();

  return (
    <div className={styles.wrapper}>
      <label htmlFor={id} className={styles.label}>
        {label}
      </label>
      <input
        ref={ref}
        {...delegated}
        type="range"
        id={id}
        className={styles.slider}
      />
    </div>
  );
}

export default React.forwardRef(Slider);
```