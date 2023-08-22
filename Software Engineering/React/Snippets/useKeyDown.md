
```tsx
import { useEffect } from "react";

function useKeyDown(targetKey: string, callback: () => void) {
  useEffect(() => {
    function handleEscapeKeyKeyDown(event: KeyboardEvent) {
      if (event.key === targetKey) {
        callback();
      }
    }
    window.addEventListener("keydown", handleEscapeKeyKeyDown);

    return () => window.removeEventListener("keydown", handleEscapeKeyKeyDown);
  }, [callback, targetKey]);
}

export default useKeyDown;
```