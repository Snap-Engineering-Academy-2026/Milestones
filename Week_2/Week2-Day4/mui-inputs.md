# User Input with Material UI

So we've learned about buttons, but what about other forms of user input?

Well, Material UI has a lot of common inputs premade for us! However, unlike buttons, most other types of input need a state variable to help keep track of what the user input is. For example, Text Fields need a string state variable to keep track of what a user has typed.

Some examples of inputs that need state variables:
 - [Text Fields](https://mui.com/material-ui/react-text-field/) - a string (or number) for what the user has typed
 - [Toggle Buttons](https://mui.com/material-ui/react-toggle-button/) - a string/array of strings of which options are toggled 
 - [Select Dropdowns](https://mui.com/material-ui/react-select/) - a value of what option was selected
 - [Checkboxes](https://mui.com/material-ui/react-checkbox/#controlled) - a boolean for checked/not
 - [Sliders](https://mui.com/material-ui/react-slider/) - a number for where the slider is in the range

<br/>

# Building a Search Bar

To practice using state variables with inputs, you're going to add a search bar to search the cards in your app!

<br/>

## 1 - Text Field

As a first step, add a Text Field to your app. Don't worry about the state variable yet, just make sure you're happy with how it looks. _Yours doesn't have to look like mine!_

<img width="1234" alt="image" src="https://github.com/user-attachments/assets/ed296d97-aa57-478e-b0d1-09314e285109" />

<br/>

<br/>

<br/>

## 2 - Text Field with State Variable

Next, add a state variable so your text field can remember what the user has typed. Use `console.log` to make sure the state variable is working. **The Material UI documentation has an example of this**, but you'll have to look around for it! _Learning how to scan documentation and identify what's most helpful for you is an important skill to develop._

<table><tr><td>
<details>
  <summary>Training Wheels</summary>

  <br/>

  As hinted above, most of Material UI's Text Field examples don't show the Text Field working with a state variable.

  It turns out, the example we want is the "Controlled" Text Field. [Here's a direct link to that part of the documentation](https://mui.com/material-ui/react-text-field/#uncontrolled-vs-controlled).

  In addition to the state variable, that example also shows how to use the `value` and `onChange` props too. Both are needed, but `onChange` is doing more work. You must pass a "change handler" function to `onChange`, and that function is called whenever the Text Field changes (from the user typing or deleting a character). The change handler automatically gets a parameter, usually named `e`, that holds information about the "change event". From this variable, we can get the new input value with `e.target.value` and remember it by putting it in our state variable.
  
  <br/>

</details>
</td></tr></table>

<img width="1234" alt="image" src="https://github.com/user-attachments/assets/8eb12397-3bbc-4bc6-b54a-9f69a4e25520" />

_In my image, you can see that my console.log is happening twice. This only happens when working on the code as a developer, and it's actually intended to help catch unintended side effects. When the app is published it'll work normally._ 

_Your console.log might also lag one letter behind the input depending on where you put it. This is also "working as intended" but for a different reason, but understanding why will help you understand other bugs with state variables in the future._

<br/>

<br/>

<br/>

## 3 - Searching!

Now that we can access what the user has typed because of our state variable, it's time to use that to filter what is shown to the user!

There are a lot of different ways to do this, but basic idea is to make a new array that only holds the data objects that match what we searched for. Then, instead of using `.map()` on the original array of data, we use `.map()` on the new filtered array instead. If the user hasn't searched for anything yet, the filtered array should just be a copy of the original.

<table><tr><td>
<details>
  <summary>Training Wheels</summary>

  <br/>

  There are multiple approaches to this, so I still want to offer options, but here are some tips:

   - We should write code inside the App component, after our state variables are created but before the `return`. The reason is because we need to be able to access the state variable (by going after) but change some things before the component is rendered (aka before the `return`).
   - **Filtering option 1:** Create an empty array, then loop through the original, adding the elements that match what was searched for. If the search term is empty add everything
   - **Filtering option 2:** Create a copy of the original array, then remove anything that doesn't match the search term
   - **Filtering option 3:** Look up the `.filter()` array function and use that
   - Don't forget to change the `.map()` to use the new filtered array.
  
  <br/>

</details>
</td></tr></table>

<img width="1431" alt="image" src="https://github.com/user-attachments/assets/c214f56c-ea05-41f0-9a1c-0b1178f9d68c" />

<img width="1431" alt="image" src="https://github.com/user-attachments/assets/79e928cb-caa0-472d-a067-3234a908eeb8" />

<br/>

<br/>

<br/>

## 4 - Optional Extras

Can you make the search work for more than just the title/name of the card data? See if you can make it search the description too

Try to make your search have autocomplete with [MUI's Autocomplete](https://mui.com/material-ui/react-autocomplete/) component
