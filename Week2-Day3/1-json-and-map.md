# Using A Separate Data File

Previously, you made a custom `DataCard.jsx` component with props to display multiple pieces of data from your project. However, that data is still technically "hardcoded" in your `App.jsx` file.

To bring us closer to real world practice, we want you to create a separate data file containing your data, then import that file in `App.jsx` and use it as the source of the data to display. In web development, an extremely common data format is called JSON, or JavaScript Object Notation, so your file should be a `.json` file.

You can look at my example `protagonists.json` file:

<table><tr><td>
<details>
  <summary>protagonists.json</summary>
  
```json
[
  {
    "title": "Miles Morales",
    "pic": "https://i.imgur.com/56chgMj.png",
    "description": [
      "Definitely Not Spiderman",
      "\"Lanky Puberty Boy\" vibes",
      "Can't do it on demand",
      "Elite music taste"
    ]
  },
  {
    "title": "Moana Waialiki",
    "pic": "https://i.imgur.com/zuscNPl.png",
    "description": [
      "Glass half full kinda gal",
      "Lackluster chicken mom",
      "Spaces out looking at water",
      "Never really knows why"
    ]
  },
  {
    "title": "Hiro Hamada",
    "pic": "https://i.imgur.com/SaYqUTP.png",
    "description": [
      "Saved by a flying pillow. Again.",
      "Has epic bedhead",
      "Hiro = Hiccup, Baymax = Toothless",
      "Neeeeeeeeeeeeeeeerd"
    ]
  }
]
```
  
  <br/>

</details>
</td></tr></table>

I import this file with this line at the top of my `App.jsx`

```jsx
import characters from "./protagonists.json";
```

<br/>

## 1 - Create, Import, Print

**Here's what you should do:**
 - Create your own JSON file with your data. _You can use ChatGPT to speed up converting your original source data into the JSON format, just check for errors._
 - import your JSON file into your `App.jsx`
 - Use `console.log` it to make sure it works ex:

```jsx
console.log("My data:", characters);
```

<img width="1422" alt="image" src="https://github.com/user-attachments/assets/09712870-0ebc-482c-bd24-0aa884d4cf92" />

<br/>

<br/>

<br/>

## 2 - Access and Display JSON Data

Now it's time for you to display the data! _You only need to do this for one of your cards, because we'll use a new concept to display all of the data in the next step after this._

Here's what it looks like for my example:

```jsx
<Grid>
  <DataCard
    title={characters[0].title}
    imageURL={characters[0].pic}
    description={characters[0].description}
  />
</Grid>
```

<br/>

<br/>

<br/>

# Dynamic Data Display With .map()

Remember `.map()` from Wednesday week 1? Well, `.map()` is great here because it lets us make a function to transform each element of an array. We have an array of data, and we want to transform each piece of data into a DataCard component. 

<br/>

## 3 - Review .map() and arrow functions

Last week, you saw how to solve this basic .map() [problem to double the value of each element in the array](https://www.codewars.com/kata/53951fff369894e4f10007a9), using this code:

```js
function doubleOneNum(num) {
  return num * 2;
}

function double(array) {
  let doubledArray = array.map(doubleOneNum);
  return doubledArray;
}
```

However, `.map()` is commonly used with another fancy piece of syntax called arrow functions ([learn more here](https://www.learn-js.org/en/Arrow_Functions)). Using arrow functions, I could write the same code like this:

```js
const doubleOneNum = (num) => {
  return num * 2;
}

function double(array) {
  let doubledArray = array.map(doubleOneNum);
  return doubledArray;
}
```

Also, `doubleOneNum` is technically just a variable, so we can remove it and just put the arrow function inside `.map(  )`:

```js
function double(array) {
  let doubledArray = array.map((num) => {
    return num * 2;
  });
  return doubledArray;
}
```

When an arrow functions only has one line, to return the new value, we can actually shorten it even more, getting rid of the curly braces and `return`. _This is called ["implicit return"](https://demirels-organization.gitbook.io/javascript-tutorial/implicit-return)_

```js
function double(array) {
  let doubledArray = array.map((num) =>
    num * 2
  );
  return doubledArray;
}
```

Just for fun, let's also get rid of the variable `doubledArray`:

```js
function double(array) {
  return array.map((num) =>
    num * 2
  );
}
```

Crazy! Here are [some more examples of `.map()` and arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map#examples) if you want to check em out.

<br/>

## 4 - Practice .map() and arrow functions

Last week, we gave you this problem to work on, make sure you've finished it!

[Normalize Name Capitalization](https://www.codewars.com/kata/6853343412b719df2f717a6e)

For extra practice:
 - Solve Normalize Name Capitalization again using arrow functions
 - Solve this other [.map() problem to greet developers with their favorite coding language](https://www.codewars.com/kata/coding-meetup-number-2-higher-order-functions-series-greet-developers), use arrow functions!
 - Solve this [harder .map() problem](https://www.codewars.com/kata/572fdeb4380bb703fc00002c), use arrow functions!

_You don't need to do all of these! Feel free to move on once you've solved the Normalize Name Capitalization problem, and come back here to practice more if you think you need it._

<br/>

## 5 - Use .map() in React

Now it's time to use `.map()` in your React code!

While we've mostly been using `.map()` to make smaller transformations, like doubling a number or modifying a string, it's capable of much more, like transforming a piece of data into a Card component.

To get a feel for how this will work, here's an example that uses `.map()` to get my DataCard's `title` prop from my imported JSON file, but the `imageURL` and `description` props are still hardcoded.

```jsx
<Grid spacing={4} container>
  {characters.map((character) => (
    <Grid>
      <DataCard
        title={character.title}
        imageURL={"https://i.imgur.com/zuscNPl.png"}
        description={[
          "Glass half full kinda gal",
          "Lackluster chicken mom",
          "Spaces out looking at water",
          "Never really knows why",
        ]}
      />
    </Grid>
  ))}
</Grid>
```

Which would look like this: _Red circles drawn afterwards for emphasis._

<img width="1422" alt="Screenshot 2025-06-25 at 12 02 36 AM" src="https://github.com/user-attachments/assets/dce91fd5-ba5f-4909-b5dd-06608a814d8d" />

<br/>

<br/>

<br/>

## 6 - Finish refactoring with .map()

Finish what you started in part 5 until all of `DataCard`'s props come from your imported JSON file.

When you're done, your page should look the same, but your `App.jsx` code should be even shorter. Now, instead of 3+ lines creating `DataCard` components, now `App.jsx` just has one line creating `DataCard`, inside the `.map()` call.

<img width="1422" alt="image" src="https://github.com/user-attachments/assets/034d8a96-c02f-4d5c-9d7f-a79c7962ab08" />

<br/>

<br/>

<br/>

# FIN

Finish early? 
 - Add more pieces of data to your JSON and watch as `.map()` makes the new cards for you automatically!
 - If one of your DataCard props is an array, like `description` in my example, see if you can figure out how to use `.map()` in `DataCard.jsx` too!
