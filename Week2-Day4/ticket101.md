# Ticket 101: Add "Favorite" Feature Based on User Feedback

**Priority:** Medium  
**Type:** Feature  
**Status:** Open  
**Assigned To:** You!  
**Difficulty:** 🟢 Beginner-Friendly

---

## 🧩 Background

Thanks to recent user feedback, we’ve learned that users want to save or “favorite” characters they like the most.

Currently, our app displays character cards from a JSON file. Each card includes a title, description, and image.

**Your task:** Add a “Favorite” button to each card that lets users toggle whether that character is a favorite.

---

## ✅ Requirements

- [ ] Update the JSON file to include a new boolean property called `favorite` for each character.
- [ ] Display a “Favorite” button below each character card.
- [ ] When the button is clicked, toggle the favorite status for that character.
- [ ] Update the button label to show if a character is “Favorited” or not.

---

## Lead Engineer Advise

### 1. Update the JSON File

Our lead engineer Ghost, is recommending we add a new property to each of our existing data in our database. The field should help us track our favorite status.

<details>
<summary><strong style="color: gray;">Ask An Engineer for help 1</strong></summary>
In `src/protagonists.json`, add a new `"favorite"` property to each object.

```json
[
  {
    "title": "Mario",
    "description": "Plumber from the Mushroom Kingdom.",
    "pic": "https://example.com/mario.png",
    "favorite": false
  },
  {
    "title": "Link",
    "description": "Hero of Hyrule.",
    "pic": "https://example.com/link.png",
    "favorite": false
  }
]
```

</details>
Ghost is also recommending that the state is handled only in the parent component. They don't want to see any props being passed down, Ghost wants a solution fast and doesn't care if it isn't the most optizmized.Hmm...where should our data be imported?

<details>
<summary><strong style="color: gray;">Ask An Engineer for help 2</strong></summary>
Import your data into `App.jsx`. Please don't copy and paste, this a general example and not specific to your data naming

```json
import charactersData from "./protagonists.json";
import { useState } from "react";

const [characters, setCharacters] = useState(charactersData);

```

</details>

### 2. Add a function to handle favorite state

In `App.jsx`, create a function that toggles the favorite value when the button is clicked. Ghost has provided a function signature to help us get started with toggling state

```js
const toggleFavorite = (index) => {
  //
};
```

Inside toggleFavorite:

- Create a new copy of the characters array so we don't mutate state directly
- Access the character at the given index
- Flip the value of its "favorite" key (true becomes false, false becomes true)
- Save this new array as the new state using setCharacters

### 3. Conditional Rendering

Lastly, Ghost has left you with this last piece of insight to tackling your first ticket.
Conditional rendering means showing different content in the UI based on some condition (like true or false).

In React, this is often done using the ternary operator:

```js
condition ? showThis : showThat;
```

Think of it like:

"If this is true, do the first thing; otherwise, do the second thing."

#### 🔍 Real-World Example (Guided, Not Full Answer)

Imagine you're looping through a list of characters and displaying a card for each one. Now you want to show a different button label depending on whether that character is favorited or not.

You might do something like this PER card (note: this is not the full solution, just a hint):

```js
<Button onClick={/* your toggle function here */}>
  {character.favorite ? "Show this when true" : "Show this when false"}
</Button>
```

#### What This Code Does:

The character.favorite is a boolean (true or false).

- If it’s true, it shows the left side of the ? (e.g., "★ Favorited").

- If it’s false, it shows the right side of the : (e.g., "☆ Favorite").

- This lets you show a different UI depending on state without writing an if-else block.


