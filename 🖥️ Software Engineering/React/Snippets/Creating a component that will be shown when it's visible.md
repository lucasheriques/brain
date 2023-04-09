```js

function Toasty() {
  // Your goal is to update the `isShown` state variable,
  // based on the user's scroll position, using
  // IntersectionObserver.
  const [isShown, setIsShown] = React.useState(false);
  const toastyRef = React.useRef();

  React.useEffect(() => {
    const observer = new IntersectionObserver((entries) => {
      const [entry] = entries;

      setIsShown(entry.isIntersecting);
    })

    observer.observe(toastyRef.current);
  }, []);

  // This CSS value will control whether the ghost is
  // visible or not.
  const translateX = isShown ? '0%' : '100%';

  return (
    <div className={styles.wrapper} ref={toastyRef}>
      <div
        className={styles.character}
        style={{
          transform: `translateX(${translateX})`,
        }}
      >
        👻
      </div>
    </div>
  );
}

```