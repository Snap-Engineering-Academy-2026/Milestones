# Ticket 102: Add Toggle View for Favorite Characters

## Background

In response to **Ticket 101**, we successfully allowed users to click a button to mark a character as a "Favorite". The `favorite` property was stored in each character object in memory using `useState`.

However, after user testing, we received the following feedback:

> _“I can favorite characters now, but there's no way to *see just my favorites*. It feels incomplete.”_

To improve the user experience, we want to allow users to **toggle between viewing all characters and just their favorites**.

---

## Acceptance Criteria

- [] Add a **toggle button** that lets the user switch between:
  - **All Characters**
  - **Only Favorited Characters**
- [] The button text should change based on the view mode.
- [] This should **not** affect the ability to favorite/unfavorite characters in either view.

---

## Ghost Engineering Advice

### 1. Add a `showOnlyFavorites` state variable

Don't peak yet, this hint will not disapppear like our snaps. Give it your best try to figure the syntax of create a state variable.

<details>
<summary><strong style="color: gray;"> Hint</strong></summary>

We add this boolean state to determine the current view mode.

```js
const [showOnlyFavorites, setShowOnlyFavorites] = useState(false);
```

</details>

### 2. Add a toggle button above the grid

In ticket101 a Material UI button that flips the state and updates the label dynamically for our favorite button now let add a show favorite button/ show all button.

<details>
<summary><strong style="color: gray;"> Hint</strong></summary>

```js
<Button
  variant="outlined"
  onClick={() => setShowOnlyFavorites(!showOnlyFavorites)}
  sx={{ mb: 2 }}
>
  {showOnlyFavorites ? "Show All Characters" : "Show Only Favorites"}
</Button>
```

</details>


### 3. Add toggle functionalilty to the `displayedCharacters` variable
This variable will decide which characters to show based on showOnlyFavorites. Look at your previous milestones to aid you through this( we will be filtering similar to a search function).

Declare a new variable called `displayedCharacters`. It decides which characters to show on the screen, based on whether the user wants to see only favorites or all character hint `displayedCharacters` will be set to a function.

<details>
<summary><strong style="color: gray;"> Ghost wrote some psuedocode</strong></summary>
```md
If the toggle (showOnlyFavorites) is true:
    Go through the characters array
    Only keep characters where character.favorite is true
    Set displayedCharacters to that filtered list
Otherwise:
    Set displayedCharacters to the full characters array
```
</details>

### let's give you an example:

```
const characters = [
  { title: "Mario", favorite: true },
  { title: "Link", favorite: false },
  { title: "Samus", favorite: true }
];
```

If `howOnlyFavorites === true`, then `displayedCharacters` will be:

```
[
  { title: "Mario", favorite: true },
  { title: "Samus", favorite: true }
]
```

If `showOnlyFavorites === false`, then `displayedCharacters` will be:

#### This approach:

- Keeps your UI logic clean by separating what’s displayed from what’s stored.

- Avoids modifying the original list of characters.

- Makes it easy to toggle views without reloading or restructuring data.

### Now use state to update the UI
Using the `displayedCharacters` variable use that to map over the favorite character allowing users to switch between the whole data vs the favorited data. You will also have to update you toggle function to account for state.
