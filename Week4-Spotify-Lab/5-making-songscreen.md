# Checkpoint 5 : Display SongScreen

Now we can get into making the new screen to show all the song details!

We’ll make a simple version first to test out our setup, and add the song details later. 

## Testing a simple new screen component

1. Make a new file (SongScreen.js) for our new <SongScreen> component, and have it return a single <Text> component. The SongScreen component should return something like this:
```
<Text>This is SongScreen</Text>
```
*Don’t forget your imports!*

2. Check that SongScreen is working by importing it into `App.js` and temporarily replacing the reference to `HomeScreen` with `SongScreen`.

3. Your app should now just show the text "This is SongScreen"

4. Change it back to using `HomeScreen`

5. Add a second `<Stack.Screen>` to your `App.js`, but have it reference `SongScreen` instead. `App.js` should have two `<Stack.Screen>`s when you're done, but you won't be able to see SongScreen anymore, because we can only show one screen at a time, and we haven't coded any buttons to change screens. (See [this example from the documentation](https://reactnavigation.org/docs/stack-navigator/?config=dynamic#usage))

## How do our users get to SongScreen? 

We want to open SongScreen when we tap on a song from HomeScreen. We want the screen to open if we tap anywhere on a `<Song> `in `<SongList>`. We can do this with a Pressable component.
Tapping anything inside a `<Pressable>` will trigger the Pressable’s onPress function:
```jsx
  <Pressable onPress={handlePress}>
  // tapping anything in here will call handlePress()
  </Pressable>
```

Let’s wrap everything inside of `<Song>` with a `<Pressable>`

```jsx
// (Song.js)

function handlePress() {
  console.log("You touched me!")
}

return (
  <Pressable onPress={ handlePress }>
    // the stuff inside of Song
  </Pressable>
);
```

