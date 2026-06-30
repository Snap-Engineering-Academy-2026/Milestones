# Text Fields and Other Inputs

In this milestone, we're going to walk through a quick example of how to use the Text Field input component, with a pattern that applies to other inputs like Select.

## Start by creating a new vite project

Using your terminal create a new vite project.

```
npm create vite@latest
```

Once the project is created go ahead and empty out the contents of `app.js`. Don't forget to install the vite packages as well. We are also going to be using materialUI so we will need to install it into our project

```
npm install @mui/material @emotion/react @emotion/styled
```

## Text Field Documentation

The MUI documentation for the text field is a bit funky.

[text field documentation](https://mui.com/material-ui/react-text-field/)

Weirdly, most of the documentation's examples are visual, and don't actually show how to get Text Fields to work properly! For that, we need to scroll down to the "Uncontrolled vs Controlled" section:

[uncontrolled vs controlled](https://mui.com/material-ui/react-text-field/#uncontrolled-vs-controlled)

Here we can see a working example of a Text Field that puts the user input in a state variable! _Make sure to change the example code to JS (JavaScript) instead of TS (TypeScript) too._

## Making a working Text Field

1. First we need to import TextField at the top of our file:

```js
import TextField from "@mui/material/TextField";
```

2. Now, let's place the `<TextField>` component in our JSX (This is copied from the MUI docs)

```jsx
<TextField
  id="outlined-controlled"
  label="Name"
  value={""}
  onChange={(event) => {
    // empty for now
  }}
/>
```

3. Check that the TextField appears on your page where you want it to go.

4. Now that we know the TextField looks right, let's add a state variable

```js
const [name, setName] = useState("Cat in the Hat");
```

Then change the `value` field in the `<TextField>` component to use our state variable.

| Before       | After          |
| ------------ | -------------- |
| `value={""}` | `value={name}` |

5. Check that the TextField now shows "Cat in the Hat" by default.

6. Now let's connect it to the state variable. Inside of our `onChange`, we'll use `setName` to update the state variable whenever the user changes the TextField.

```jsx
  onChange={(event) => {
    setName(event.target.value);
  }}
```

7. If you've done this right, the state variable `name` should now be accessible and it will have whatever the user types in the text field!

## Use it with your fetch!

Now that you have user input as a state variable, use it in your fetch requests!

Here's an example to search for books with titles that match the name in the input we made above:

```js
const requestOptions = {
  method: "GET",
  redirect: "follow",
};

fetch(
  "https://openlibrary.org/search.json?q=" + name + "&limit=10&fields=title",
  requestOptions,
);
```

Using JSX we can make this endpoint more readable:

```js
`https://openlibrary.org/search.json?q=${name}
        )}&limit=10&fields=title`;
```

Sample Result - https://openlibrary.org/search.json?q=cat+in+the+hat&limit=10&fields=title

At this point, the code is incomplete, we haven't finished chaining our promise! We need to handle our promise state - look back at the slide if you a little lost here. I'll drop these hints to help get you started. Fill out the items needed to make this code run!

```js
import TextField from "@mui/material/TextField";
import Button from "@mui/material/Button";
import { useState } from "react";

function App() {
  const [funFact, setfunFact] = useState("");

  const searchDogFunFact = () => {
    fetch(`API HERE`)
      .then()
      .then(PLEASE LOG YOUR DATA HERE)
      // this error function is pretty standard so I will leave this here
      .catch((error) => console.error(error));
  };
  // add a log to check your state
  return (
    <>
      <TextField
        label="Search"
        value={""}
        onChange={(event) => setfunFact(event.target.value)}
      />
      {/* Add a button to your page, here the button will trigger the fetch */}
      <Button onClick={searchDogFunFact}>Search</Button>
    </>
  );
}

export default App;
```

## Map through you API results

Now that we have fetched the data, map through the data and display your data

## Try it with other inputs!

Get another example working for one of these other input components:

- [Slider](https://mui.com/material-ui/react-slider/) - input a number by dragging a slider
- [Select](https://mui.com/material-ui/react-select/) - select from a dropdown list of predetermined options
- [Radio Group](https://mui.com/material-ui/react-radio-button/) - choose from a list of predetermined options
- [Full list of input components](https://mui.com/material-ui/all-components/#inputs)

</br>
