# Forms and Validations

In this milestone, we are going to learn how to handle different types of form inputs and handle validation for those inputs.

<br/>

## 1 - Introducing Inputs (Handler Functions)

Much like in the previous Milestone, there is an `onChange` prop that you can add to inputs to detect when a user types information into it. 
We will use "handler" functions just like before to handle the change. Below is an example of text input implemented with a `handleName` function.

```jsx
export default function Form(){
  const [fullName, setFullName] = useState("");

  const handleName = (e) => {
    const {value} = e.target //NEW!
    setFullName(value)
  }
  return(
    <>
      <Typography variant="h5" sx={{ mb: 1 }}>
          Full Name
      </Typography>
      <TextField
          type="text"
          name="fullName"
          value={fullName} // NEW!
          onChange={handleName}
      />
    </>
  )
}
```
You will notice two new aspects from before. 
 - Destructuring a `value` CONST from the event variable in the `handleName` function
 - A `value` PROP set to a state in the `<TextField> prop`
The `value` PROP allows us to get the entire value of the input on every change and the `value` CONST gets us that input information

<br/>

But this implementation is only for one input, for one input we had to create a handle function for the `onChange` 
prop and create state for the input. If we were add another input field for instance for a numeric input, what would
we need to add?
<details>
<summary>Reveal Answer</summary>
The numeric input would require a separate handler function AND a separate state!
In fact, with our current knowledge every new input would require its own
handler function and state
</details>

<br/>

## 2 - Handling Multiple Inputs (One state / One Handler)
```jsx
export default function Form(){
  const [values, setValues] = useState({ fullName: "", quantity: "" });

  const handleChange = (e) => {
    const {name, value} = e.target
    const newValues = { ...values, [name] : value };
    setValues(newValues);
  }
  return(
    <>
      <Typography variant="h5" sx={{ mb: 1 }}>
          Full Name
      </Typography>
      <TextField
          type="text"
          name="fullName"
          value={values.fullName}
          onChange={handleChange}
      />
      <Box>
        <Typography variant="h5" sx={{ mb: 1 }}>
          Quantity (Tickets)
        </Typography>
        <TextField
          type="number"
          name="quantity"
          value={values.quantity}
          onChange={handleChange}
        />
      </Box>
    </>
  )
}
```
Let's breakdown the big changes into two parts!
1. Using an object to keep state for multiple inputs into a single state
```jsx
const [values, setValues] = useState({ fullName: "", quantity: "" });
```
Since we now have two inputs, our object has two key-value pairs.
Number of inputs = Number of Key-Value pairs
> [!NOTE]
> Note that the keys of the object match the `name` prop of the inputs

2. Consolidating multiple `handle` functions into a single `handleChange` function
```jsx
const handleChange = (e) => {
  const {name, value} = e.target
  const newValues = { ...values, [name] : value };
  setValues(newValues);
}
```
> [!NOTE]
> The `...values` syntax is known as a [spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)
> It allows us to "unwrap" or expand array and object literals
Since our state is stored inside a single object, we have to only update Key-Value
pair of associated input, we do that by creating a new object that only updates key
provided by the `name` from the event object.

<br/>

## 3 - Adding a Button for Form Submission
Now that we can use state to keep track of input data lets give the user the ability to
submit their form. Let's bring back the button!

Add the Button
```jsx
<Button
  sx={{ m:1 }}
  onClick={handleSubmit}
>
  Submit
</Button>
```
Add the handleSubmit function
```jsx
const handleSubmit = () => {
  console.log(values)
};
```
Now when you enter information in your input and click on the submit button, you should
see all your input state, represented by `values` variables, in your browser console!

Try entering information in your input and "submitting" your form to see the data be
displayed on the terminal.

<br/>

## 4 - Handling Validations on Form Submission
When user submit form information we should check to see if the information is valid.
Below we will check to see if the user left any of the input fields empty.
The `validate` function will return a object with error messages if any of the validations fail.


```jsx
const validate = ({ fullName, quantity }) => {
  const errors = {};
  // FULL NAME VALIDATIONS
  if (!fullName.trim()) {
    errors.fullName = "Full name is required.";
  }
  // QUANTITY VALIDATIONS
  if (quantity === "") {
    errors.quantity = "Quantity is required.";
  }
  return errors
}
```
<br/>

## 5 - Display error messages on Input
To display error messages to the user, we need a new state to keep track of which inputs
validations failed and what the message is.

```jsx
// NEW STATE
const [errors, setErrors] = useState({});

// CHANGED handleSubmit Function
const handleSubmit = () => {
  const newErrors = validate(values);
  setErrors(newErrors);
};
```

```jsx
<>
  <Typography variant="h5" sx={{ mb: 1 }}>
      Full Name
  </Typography>
  <TextField
      type="text"
      name="fullName"
      value={values.fullName}
      onChange={handleChange}
      error={Boolean(errors.fullName)} // NEW!!
      helperText={errors.fullName || " "} // NEW!!
  />
</>
```
> [!NOTE]  
> Two new props in our Components `error` and `helperText`
> `error` prop takes a Boolean that will toggle the componenents style to red
> `helperText` prop takes a string to display a message below the input, in this case it is used display the validation message

Below you will find the complete component with all the additions we made during the milestone. Take a look
if you are having any issues with errors.

<details>
  <summary>Training Wheels / Full Component</summary>

  ```jsx
  import { useState } from "react";
  import { Typography, TextField, Box, Button } from "@mui/material";

  const validate = ({ fullName, quantity }) => {
    const errors = {};
    // FULL NAME VALIDATIONS
    if (!fullName.trim()) {
      errors.fullName = "Full name is required.";
    }
    // QUANTITY VALIDATIONS
    if (quantity === "") {
      errors.quantity = "Quantity is required.";
    }
    return errors
  }

  export default function Form(){
    const [values, setValues] = useState({ fullName: "", quantity: "" });
    const [errors, setErrors] = useState({});

    const handleChange = (e) => {
      const {name, value} = e.target
      const newValues = { ...values, [name]: e.target.value };
      setValues(newValues);
    }
    const handleSubmit = () => {
      const newErrors = validate(values);
      setErrors(newErrors);
    };
    return(
      <>
        <Typography variant="h5" sx={{ mb: 1 }}>
            Full Name
        </Typography>
        <TextField
            type="text"
            name="fullName"
            value={values.fullName}
            onChange={handleChange}
            error={Boolean(errors.fullName)}
            helperText={errors.fullName || " "}
        />
        <Box>
          <Typography variant="h5" sx={{ mb: 1 }}>
            Quantity (Tickets)
          </Typography>
          <TextField
            type="number"
            name="quantity"
            value={values.quantity}
            onChange={handleChange}
            error={Boolean(errors.quantity)}
            helperText={errors.quantity || " "}
          />
        </Box>
        <Button
          sx={{ m:1 }}
          onClick={handleSubmit}
        >
          Submit
        </Button>
      </>
    )
  }
  ```
</details>

## 6 - CHALLENGE!
Add a new TextField component that is a type "date", add validations to make sure the entered date
is not before Today's date and display validation message if it fails. Hint you will need use of Date
object in JavaScript [Date Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

</br>

</br>

</br>

# FIN