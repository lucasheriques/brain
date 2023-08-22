```jsx
// Breadcrumbs.js
function Breadcrumbs({ children }) {
  return (
    <nav aria-label="Breadcrumbs">
      <ol>{children}</ol>
    </nav>
  );
}

function Crumb({ href, isCurrent, children }) {
  return (
    <li>
      <a
        href={href}
        aria-current={isCurrent && 'page'}
      >
        {children}
      </a>
    </li>
  );
}

Breadcrumbs.Crumb = Crumb;

export default Breadcrumbs;


// App.js
import Breadcrumbs from './Breadcrumbs';

function App() {
  return (
    <Breadcrumbs>
      <Breadcrumbs.Crumb href="/">
        Home
      </Breadcrumbs.Crumb>
      <Breadcrumbs.Crumb href="/CLYW">
        CLYW
      </Breadcrumbs.Crumb>
      <Breadcrumbs.Crumb
        isCurrent={true}
        href="/CLYW/boy"
      >
        BOY
      </Breadcrumbs.Crumb>
    </Breadcrumbs>
  );
}
```