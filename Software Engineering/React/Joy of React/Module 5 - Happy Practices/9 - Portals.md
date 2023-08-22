Portals are a way to teleport a component to a different part of the DOM. Its main use case is related to components that are floating on the screen (modals, toasts, etc).

When it comes specifically to components that are meant to float above the UI, things like modals and dropdowns and tooltips, we often use fixed or absolute positioning, to take them out of flow and position them in a precise location. But CSS has some implicit and surprising dependencies.

Libraries like HeadlessUI, Reach UI, and Radix Primitives all use portals under-the-hood to avoid this potential issue. But let's see how we could implement it ourselves, using our home-grown Modal component.

We can create a portal by using `import { createPortal } from 'react-dom';`.

`createPortal` takes 2 parameters:
- The react component you want to teleport
- A container DOM node (using something like `document.querySelector(#modal-root)`)

```jsx
import { createPortal } from 'react-dom';

function Modal({ children }) {
  return createPortal(
    // The React elements to render:
    <div className="modal">
      {children}
    </div>,
    // The target DOM container to hold the output:
    document.querySelector('#modal-root')
  );
}
```

You'll also need to edit the HTML file to create that target container:

```html
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  </head>
  <body>
    <div id="root"></div>
    <div id="modal-root"></div>
  </body>
</html>
```

Example generic Portal component:

```jsx
import React from 'react';
import { createPortal } from 'react-dom';

function Portal({ children }) {
  const [host, setHost] = React.useState(null);

  React.useEffect(() => {
    const host = document.createElement('div');
    document.body.appendChild(host);
    host.setAttribute('data-react-portal-host', '')
    setHost(host);

    return () => {
      host.remove();
    };
  }, []);


  if (!host) {
    return null;
  }
  
  return createPortal(
    children,
    host
  );
}

export default Portal;
```