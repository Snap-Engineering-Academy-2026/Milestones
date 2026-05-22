# Checkpoint 6 

Wrap everything returned in Song.js in a `<Pressable>`, put a console.log in the Pressable’s onPress, and run the code and check if you see your console.logs after tapping on a song in your list. 

## But what actually goes inside of onPress? 


Well, we want onPress to navigate us to a SongScreen that displays details about that Song. To figure this out, we’ll look at React Navigation’s docs for “Moving Between Screens.” One way to trigger a navigation would be to press on a button like the example code uses with an onPress function (the same way Pressable works!). From the documentation, we can see this example:
```jsx
function HomeScreen({ navigation }) {

  return (
    ...

    <Button
      title="Go to Details"
      onPress={() => navigation.navigate('Details')}
    />

    ...
  )
  ```
So, we could add that code to onPress in our Pressable, but we’d run into a problem. We need the navigation variable, which in the documentation’s example comes from the props to `<HomeScreen>`. We need to access navigation from the component `<Song>`, but because `<Song>`  is a child of `<SongList>`, which is a child of `<HomeScreen>`, so the navigation variable from the props of `<HomeScreen>` is very far away.


We can use the documentation to find “Access the navigation prop from any component” and see that we can use useNavigation instead like so:

```jsx
 const navigation = useNavigation();

  return (
    <Button
      title={`Go to ${screenName}`}
      onPress={() => navigation.navigate(screenName)}
    />
  );

```


Let’s update our Pressable’s onPress in Song.js to use this:
```jsx
// (Song.js)
const navigation = useNavigation();

return (
  <Pressable 
    onPress={() => navigation.navigate("SomeScreenName")}
  >

      // the stuff inside of Song

  </Pressable>
)
```

The string `"SomeScreenName"` needs to match whatever you used as the screen's name in the `<Stack.Screen>` in `App.js` 

Finish this checkpoint by putting the right name and then check it out!

We'll expand on this checkpoint in the future by showing you how to pass information about the song to `SongScreen`
