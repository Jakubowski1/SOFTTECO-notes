Simple copy to clipboard function.
```jsx
import React from "react";
import ClipboardIcon from "../svg/ClipboardIcon";
import SuccessIcon from "../svg/SuccessIcon";
import useCopyToClipboard from "../utils/useCopyToClipboard";

function CopyButton({ code }) {
  // isCopied is reset after 3 second timeout
  const [isCopied, handleCopy] = useCopyToClipboard(3000);

  return (
    <button onClick={() => handleCopy(code)}>
      {isCopied ? <SuccessIcon /> : <ClipboardIcon />}
    </button>
  );
}
```

```jsx
import React from "react";
import copy from "copy-to-clipboard";

export default function useCopyToClipboard(resetInterval = null) {
  const [isCopied, setCopied] = React.useState(false);

  const handleCopy = React.useCallback((text) => {
    if (typeof text === "string" || typeof text == "number") {
      copy(text.toString());
      setCopied(true);
    } else {
      setCopied(false);
      console.error(
        `Cannot copy typeof ${typeof text} to clipboard, must be a string or number.`
      );
    }
  }, []);

  React.useEffect(() => {
    let timeout;
    if (isCopied && resetInterval) {
      timeout = setTimeout(() => setCopied(false), resetInterval);
    }
    return () => {
      clearTimeout(timeout);
    };
  }, [isCopied, resetInterval]);

  return [isCopied, handleCopy];
}
```

here is a simple code that react when bottom of the page is reached 

```js
// utils/usePageBottom.js
import React from "react";

export default function usePageBottom() {
  const [bottom, setBottom] = React.useState(false);

  React.useEffect(() => {
    function handleScroll() {
      const isBottom =
        window.innerHeight + document.documentElement.scrollTop 
        === document.documentElement.offsetHeight;
      setBottom(isButton);
    }
    window.addEventListener("scroll", handleScroll);
    return () => {
      window.removeEventListener("scroll", handleScroll);
    };
  }, []);

  return bottom;
}
```
