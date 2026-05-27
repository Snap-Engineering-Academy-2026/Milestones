# Adding a Stack Navigator 4 : Get SongScreen to display 

Now it’s time to install the specific packages needed for StackNavigation. This is what will let us go back and forth between our home screen and the screen details screen we'll be making.

## Installing Stack Navigation Dependencies

1. Follow the [installation steps for Stack Navigator](https://reactnavigation.org/docs/stack-navigator/?config=dynamic#installation) for "Expo managed projects" cuz we use Expo for our project. (This means ignore anything that's for "Bare React Native" projects)  
   *Read the documentation carefully to figure out what steps are needed and which are not! We only need 3 of them. To help you out, one is a `yarn` terminal command, another is an `npx` terminal command, and the last is adding a line of code to the top of our `App.js`*
 
2. If we look at [the first example](https://reactnavigation.org/docs/stack-navigator/?config=dynamic#installation) in the documentation, notice that the example is a component called `MyStack` and not `App`, like in our code. Normally we want you to learn from the documention as much as possible, but there's a couple of subtle differences like this between our code and the documentation examples that make things confusing. So we'll walk you through the next steps a bit more carefully.

3. There are several pieces we need in order for a Stack Navigator to work. Add these snippets to your `App.js` as you go:  
    - Importing the `createStackNavigator` function:
    ```js
    import { createStackNavigator } from '@react-navigation/stack';
    ```
    
    - Using that function to get the Stack component reference
    ```js
    const Stack = createStackNavigator();
    ```

    - The `<Stack.Navigator>` parent/wrapper component
    ```jsx
    <Stack.Navigator>
        ...
    </Stack.Navigator>
    ```

    - The `<Stack.Screen>`s reference the different components we want as screens. These must be children of a `<Stack.Navigator>`. We only have one "screen" right now, which is `HomeScreen`, so let's replace `<HomeScreen/>` in our `App.js` with a `Stack.Screen` that references it.
    ```jsx
    <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} />
    </Stack.Navigator>
    ```

4. Test your app to make sure it works. Your app should still look the same, but your App.js should now have the `Stack.Navigator` and `Stack.Screen` added to it (all inside of the `<NavigationContainer>` from earlier. **The last two milestones have all just been setup so far!** Crazy how much more complicated "navigating" to a page is without links/URLs right?
