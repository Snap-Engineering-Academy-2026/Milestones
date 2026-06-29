# Fetch data on first page load with useEffect!

One thing you all may have run into is getting data from your API to show up when your **first** load the page!

While there isn't an obvious or inituitive way to do this, React does make it relatively straightforward.

The trick is to use another hook called `useEffect()` (The other hook we've used so far is `useState()`)

## Using useEffect()

It's pretty simple! First import `useEffect()` from React. In this case I import it alongside `useState()`.

```js
import { useState, useEffect } from "react";
```

Then you use it like this in your code:

```jsx
const [data, setData] = useState([]);

useEffect(() => {
  // Everything in here gets run once on first page load
  fetch("https://uselessfacts.jsph.pl/api/v2/facts/random", requestOptions)
    .then((response) => response.json())
    .then((result) => {
      console.log("got data", result);
      setData(result);
    })
    .catch((error) => console.log("error", error));
}, []);
```

## Docs

[useEffect Documentation](https://react.dev/reference/react/useEffect)

As a note, the documentation page for useEffect() contains some pretty complicated examples. The vast majority of the time, all you'll need is the much simpler example above.
