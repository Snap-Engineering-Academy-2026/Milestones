# Navigation Setup

## Background

Check out App.js in the starter code! It’s simple for now, it just has a <HomeScreen> component and that’s it.

The <HomeScreen> component uses the connection we made with Spotify earlier and to get some of data from our Spotify account. It fetches a list of your most listened songs and passes that to the <SongList> component.
The <SpotifyAuthButton> component is another screen that’s part of the home screen. We display it if the user hasn’t signed in with Spotify yet
The <SongList> component displays the songs given to it (in data form) by stacking many <Song> components vertically top of each other.
The <Song> component displays one song (in data form) as a horizontal box with an album picture, song title, and artist. 

## Lab Goal: Make a new screen to display song details

What if we want to see more information about a song? The songs details are hard to read, we want to be able to tap on a song and open an expanded view of it.

To make new screens, we need something called “navigation.” The most common library for this is called React Navigator. Looking at [React Navigator's docs for StackNavigator](https://reactnavigation.org/docs/stack-navigator/), we see we also first need to install [some other base dependencies](https://reactnavigation.org/docs/getting-started/). Follow the steps for “Installing dependencies into an Expo managed projects”

We want to setup "Navigation" in our app so we can make multiple screens! In our case, we're going to add a "Song Details" screen to our app so that when we tap on a song in our list, we're taken to a screen that shows the details for that song.

<br/>

<br/>

<br/>

## Install Generic Navigation Dependencies:

Follow the [installation steps for the generic navigation packages](https://reactnavigation.org/docs/getting-started#installation).
<details> 
    <summary> Training Wheels </summary>
    
First find the command in the documentation to install `@react-navigation/native` with `npm` and do that  

Next, follow the instructions for "Installing dependencies into an Expo managed project"

</details>

<br/>

<br/>

<br/>

## Setting up NavigationContainer

At the bottom of the "Getting Started" documentation page, you can see that we now need to choose either "Static Configuration" or "Dynamic Configuration" for our navigation.

For this lab, **we always want the "Dynamic" option**, and we recommend you use that for other projects too. "Static" is less common so there's less information about it, and most apps will end up needing the additional options that "Dynamic" offers anyway.

1. So, we choose "dynamic" and [go to this page](https://reactnavigation.org/docs/hello-react-navigation/?config=dynamic). There's now some more things for us to install with `npm`, so do that.

2. The next step is a bit confusing. The documentation shows an example with several new things, notably `<NavigationContainer>` and `createNativeStackNavigator()`. Let's start with `<NavigationContainer>` and ignore everything else.

In order for navigation to work, we need to "wrap" our whole app in a `<NavigationContainer>`. To do this, go to `App.js` and do the following:
 * Import `NavigationContainer` at the top of the file (copy from the documentation example!)
 * Add a `<NavigationContainer>` as a parent "wrapping" the `<HomeScreen/>` component.
 * Run it to check for errors.

*Remember that parent/child components are nested like this:*
```jsx
<ParentComponent>
    <ChildComponent>
</ParentComponent>
```

When you're done with this Checkpoint, your app should work and look the same, but your App.js will be different because it has a `<NavigationContainer>` now.

In the next checkpoint, we'll add the next layer we need for navigation, called a Stack Navigator.

<br/>

<br/>

<br/>

## FIN

Yay!
