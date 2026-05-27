# Your Own Custom Component

The Cards we’re using to display our data are getting complicated and repetitive. We're going decompose our code by making a new custom component in a new file.

Goals of this milestone:
 - Learn how to make your own component with props
 - Use it to refactor your code from looking like the left example to the right example!

<br/>

<p align="center">
  <img alt="Old" align="top" src="https://github.com/user-attachments/assets/3a7539f1-cfab-43e2-bcc6-1270acf3aba4" width="46%">
&nbsp; &nbsp; &nbsp; &nbsp;
  <img alt="New" align="top" src="https://github.com/user-attachments/assets/8d9e268b-ea0c-41b2-a4f1-a55591f9e8ef" width="43%">
</p>

<br/>

<br/>

<br/>

## New Component File

1. Make a new file called `DataCard.jsx`

<br/>

2. Copy/Paste the code below into the file
<table><tr><td>
<details>
  <summary>DataCard.jsx</summary>
  
```jsx
import * as React from 'react';
import Card from '@mui/material/Card';
import CardContent from '@mui/material/CardContent';
import Typography from '@mui/material/Typography';

export default function DataCard() {
  return (
    <Card>
      <CardContent sx={{ pt: 0 }}>
        <Typography>Data card placeholder</Typography>
      </CardContent>
    </Card>
  );
}
```

<br/>

</details>
</td></tr></table>

<br/>

3. This is a basic example of a custom component file. To use it, we need to import it and reference it in our code. 

   - At the top of `App.jsx`, import the new file with `import DataCard from './DataCard'`
   - Further down in `App.jsx` add the DataCard component somewhere on your page with `<DataCard />`

<img width="1479" alt="image" src="https://github.com/user-attachments/assets/eac37243-d23f-45cc-979d-7fa17bdf5e47" />

_Yours might not look exactly like this depending on where you put it, it's OK as long as it shows up._

<br/>

<br/>

<br/>

## Display Your Data 

4. Replace the basic example JSX inside DataCard with the custom Card JSX that displays your own data. Fix the errors!

<table><tr><td>
<details>
  <summary>Training Wheels</summary>
  
  <br/>
  
  The errors are import errors. Make sure all of the Material UI components your custom Card needs are imported at the top of `DataCard.jsx`. For example, if you used MUI's `<CardMedia>` component for images, you'll need to add 

```jsx
import CardMedia from '@mui/material/CardMedia';
```

  <br/>

</details>
</td></tr></table>

<img width="1479" alt="image" src="https://github.com/user-attachments/assets/9f3d5d87-f992-4e09-80d8-9692a9a382fe" />

<br/>

<br/>

<br/>

## Props

5. So, now we've moved this into a separate file, but the data displayed by `DataCard.jsx` is still hardcoded. We want to be able to use `DataCard.jsx` to display multiple different piece of data. Metaphorically, we want to add "parameters" to our function. But actually, that's closer to reality than metaphor. In React, components are literally functions, and instead of "parameters" we use **Props**. Props will feel very similar to parameters, but the syntax is slightly different. Example:

In `DataCard.jsx`:
```jsx
export default function DataCard({ text }) { // props look like parameters, but note the curly braces!
  return (
    <Card>
      <CardContent sx={{ pt: 0 }}>
        <Typography>Text prop is: {text}</Typography>
      </CardContent>
    </Card>
  );
}
```

In `App.jsx`:
```jsx
<DataCard 
    text="This is a prop!"
/>
```

Displays on the page like:

<img width="215" alt="image" src="https://github.com/user-attachments/assets/70a4c33e-9ab0-44ab-8018-2d5899da73f2" />

**NOTICE**: In `DataCard.jsx`, we insert the value of the `text` prop variable by wrapping it in curly braces ex: `Text prop is: {text}`. This is a new piece of JSX syntax. Anything in curly braces gets "evaluated as a JavaScript expression" before being displayed, not just prop variables. So `Num: {Math.sqrt(9)}` gets evaluated as JavaScript and would display on the page as "Num: 3". 

<br/>

<br/>

<br/>

6. Using the example above, add your own prop to your `DataCard.jsx` to display a value from your data. Start with something simple, like a title or image URL. Since this can require a slightly different version of using the curly brace syntax, here's an example to get you started:

```jsx
<CardMedia
  component="img"
  height="350px"
  image={imageURL}
/>
```

<table><tr><td>
<details>
  <summary>Training Wheels</summary>
  
  <br/>

  Not quite a full solution, but here's a more filled out example

  In `DataCard.jsx`:
```jsx
export default function DataCard({ imageURL, text }) {
  return (
    <Card>
      <CardMedia component="img" height="350px" image={imageURL} />
      <CardContent sx={{ pt: 0 }}>
        <Typography>Text prop is: {text}</Typography>
      </CardContent>
    </Card>
  );
}
```

  In `App.jsx`:
```jsx
<DataCard 
  text="This is a prop!"
  imageURL={"https://i.imgur.com/zuscNPl.png"}
/>
```
  
  <br/>

</details>
</td></tr></table>

<img width="1422" alt="image" src="https://github.com/user-attachments/assets/561f9352-ee26-4ecf-89b1-518111c99783" />

<br/>

<br/>

<br/>

7. Add all the remaining props so you can recreate your custom card completely with DataCard.

<img width="1422" alt="image" src="https://github.com/user-attachments/assets/5bcc75ce-07cb-46ec-af0c-af8df80a15db" />

<br/>

<br/>

<br/>

## Finish Refactoring

8. Now that you can recreate your custom card completely with DataCard, and you're using props for all the data, refactor your `App.jsx` code to only use DataCard and props.

Inside my example `App.jsx`:
```jsx
<Grid spacing={4} container>
  <Grid>
    <DataCard
      title="Miles Morales"
      imageURL={"https://i.imgur.com/56chgMj.png"}
      description={[
        "Definitely Not Spiderman",
        '"Lanky Puberty Boy" vibes',
        "Can't do it on demand",
        "Elite music taste",
      ]}
    />
  </Grid>
  <Grid>
    <DataCard
      title="Moana Waialiki"
      imageURL={"https://i.imgur.com/zuscNPl.png"}
      description={[
        "Glass half full kinda gal",
        "Lackluster chicken mom",
        "Spaces out looking at water",
        "Never really knows why",
      ]}
    />
  </Grid>
  <Grid>
    <DataCard
      title="Hiro Hamada"
      imageURL={"https://i.imgur.com/SaYqUTP.png"}
      description={[
        "Saved by a flying pillow. Again.",
        "Has epic bedhead",
        "Hiro = Hiccup, Baymax = Toothless",
        "Neeeeeeeeeeeeeeeerd",
      ]}
    />
  </Grid>
</Grid>
```

<img width="1422" alt="image" src="https://github.com/user-attachments/assets/d58d13ef-6b6a-4dd0-9b24-f3b32c4ebb4b" />

<br/>

<br/>

<br/>

9. (optional) I use an array for the `description` prop. If you have an array, try to figure out how to use `.map()` from Wednesday week 1 to generate the JSX to display the data in the array in your `DataCard.jsx`. _For this particular step, you can also try to get ChatGPT to write the code that uses `.map()`, then make sure it works and ask questions to understand how it works._


# FIN!
