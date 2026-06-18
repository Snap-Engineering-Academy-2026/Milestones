# Clicks and State

In this milestone, we're going to learn about handling click events and variables. But first, lets install a React Devtools Extenstion for Chrome. This is a Chrome only extension but will help out immensely with creating React programs. Find the link below!

[Chrome React Devtool](https://react.dev/learn/state-a-components-memory#meet-your-first-ho0ok](https://chromewebstore.google.com/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en))


<br/>

## 1 - First Click

In React, you can add the `onClick` prop to almost any element to detect when the user clicks on it. The value of the `onClick` prop must be a function, which we usually call the "click handler." Here's a basic example with a button:

```jsx
export default function Button() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <Button
      variant="contained"
      sx={{ px: 6, mx: "auto" }}
      onClick={handleClick}
    >
      Click Me
    </Button>
  );
}
```

You can also use arrow functions:

```jsx
<Button
  variant="contained"
  sx={{ px: 6, mx: "auto" }}
  onClick={() => {
    alert("You clicked me!");
  }}
>
  Click Me
</Button>
```

Copy one of those examples into your code (or add your own `onClick` somewhere) and try it out.

<img width="1422" alt="image" src="https://github.com/user-attachments/assets/6e915eb7-8be4-49e8-b184-9005826a1d90" />

<br/>

<br/>

<br/>

## 2 - Counting Clicks

To learn about variables in React, let's make a simple click counter.

You'll need to do the following:
 - Create a new variable in your code.
 - In your click handler function, replace the `alert()` with code that adds 1 to your variable and `console.log`s it.

<img width="1422" alt="image" src="https://github.com/user-attachments/assets/ebf29bd6-052d-488c-83e9-bec5285abc20" />

<br/>

<br/>

<br/>

## 3 - Displaying Click Counter

Next, add code to display that variable somewhere on your page. Remember how to use `{ }` to do that?

<table><tr><td>
<details>
  <summary>Training Wheels</summary>

  You should have something like this in your code:
  
```jsx
<Typography variant="h5">
  Clicks so far: {count}
</Typography>
```

<br/>

</details>
</td></tr></table>

<img width="1422" alt="image" src="https://github.com/user-attachments/assets/97f7a7af-bc6d-4419-bf3e-923b93de06e2" />

<br/>

<br/>

<br/>

**Wait... why is the display always showing zero, even when my console.log shows the variable is increasing?**

<img width="1422" alt="Screenshot 2025-06-25 at 12 21 56 PM" src="https://github.com/user-attachments/assets/389d9b3b-3dbf-46dc-997e-a063e6142c59" />

<br/>

## 4 - Investigating the Click Counter

Why does the counter stay at zero?

Well, React has a concept called the "Component Lifecycle" which controls when the page is rendered (or re-rendered).

Building an understanding now will make it **much easier** for you to debug rendering errors in the future. 

Add another `console.log` that prints the value of the variable, and put it just above the `return` in your file.

**What do you notice?**

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

Don't peek down below until you know what's going on ;)

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

## 5 - State Variables

So, the problem we observed above is that even though the click handler function changes your variable, React does not re-render the component. We could see that because the `console.log` we put above the `return` in our component only happens once per refresh, at the beginning. 

We need to tell the component to re-render when we change the variable. And it turns out, React has something called "state variables" that do that for us!

<br/>

### Fix: use a state variable!

To add a state variable, there are several steps.

1. import `useState` from React ([this is called a React "Hook"](https://react.dev/learn/state-a-components-memory#meet-your-first-hook)) at the top of the file:
```jsx
import { useState } from 'react';
```
2. Just like regular variables, we have to declare state variables. But state variables are declared in a specific way. Replace:
```jsx
let counter = 0;
```
with
```jsx
const [counter, setCounter] = useState(0); // must go inside of your component! State variables cannot be global
```
> [!NOTE]  
> This line creates two things: the state variable `counter` and the function `setCounter`. The `[` and `]` syntax here is called [array destructuring](https://javascript.info/destructuring-assignment), and it's what lets two things be created on the same line.

3. Changing a state variable only works if the corresponding "setter" function is used. Replace:
```jsx
counter += 1;
```
with
```jsx
setCounter(counter + 1);
```
> [!NOTE]  
> This is the special sauce of state variables. The `setCounter` function actually does two things. It changes the `counter` variable, **and** it tells React to render the component again, to display the new value of `counter`!

4. Test it out! *The counter will feel more smooth if you comment out the `alert()` function.*

<details>
  <summary>Training Wheels / Example Solution</summary>

  ### Working with state variables!

  ```js
  import { useState } from "react";
  
  export default function Button() {
    const [counter, setCounter] = useState(0);
  
    function handleClick() {
      setCounter(counter + 1);
      // alert("Clicked! Counter: " + count);
    }
  
    return (
      <button onClick={handleClick}>
        Clicks - {counter}
      </button>
    );
  }
  ```
</details>

</br>

## 6 - State Variables with MUI

Many components rely on state variables to work. For example, Modals, Popovers, and Drawers use a boolean state variable to control if the modal is open or closed.

Choose one and add a simple example of it to your code:
 - [Modal](https://mui.com/material-ui/react-modal/)
 - [Popover](https://mui.com/material-ui/react-popover/)
 - [Drawer](https://mui.com/material-ui/react-drawer/)

<img width="552" alt="modal gif" src="https://github.com/user-attachments/assets/3bf52c30-cddb-4dee-9a7a-20011d44a3e6" />

</br>

</br>

</br>

# FIN

Further learning
- [Map and arrow function practice](https://github.com/Snap-Engineering-Academy-2025/Milestones/blob/main/Week2-Day3/1-json-and-map.md#4---practice-map-and-arrow-functions)
- Complete [these interactive challenges](https://react.dev/learn/state-a-components-memory#challenges) from the React documentation to practice debugging state variables.
