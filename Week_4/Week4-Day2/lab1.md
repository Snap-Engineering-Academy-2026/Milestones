# ⚡️React Native Lab 1 instructions

Welcome to this crash course on how to create a mobile app with React Native! Today's lab has three parts.

# Part 1: Set Up

_This heavily adapts content from [Expo Docs](https://docs.expo.io/get-started/installation/) and [React Native Docs](https://reactnative.dev/docs/environment-setup)_.

### 1. ✨ A quick overview

We'll be using the following tools from Expo to develop apps:

1. a command line app called Expo CLI to initialize and serve your project
2. VSCode as our text editor
3. either Expo Go, which allows us to open our projects on the phone, or any web browser to open the project on the web.

### 2. 👾 In your terminal run the following commands:

```
brew install watchman
```

> **FYI:** Watchman was developed by Facebook to watch for file changes. It'll help with hot reloading later!

Make sure you have expo client installed, check by running this command. You should see a version number return:

```bash
$  expo --version
6.3.10
```

<details>
If you do not have expo-client install run the following command in your terminal :

)

```bash
$ npm install -g expo-cli
```

</details>

### 3. 📲 On your phone, download the Expo Go app:

[🤖 Android Play Store - Android Lollipop (5) and greater.](https://play.google.com/store/apps/details?id=host.exp.exponent)

[🍎 iOS App Store - iOS 11 and greater.](https://search.itunes.apple.com/WebObjects/MZContentLink.woa/wa/link?path=apps%2fexponent)

**Set up an account if needed!**

# Creating a React Native app

This command will create a new project directory named react-native-lab1, using the blank template. This template has essential boilerplate code and libraries needed to build our app, including Expo Router. We'll continue to add more libraries throughout as needed.

```
npx create-expo-app@latest react-native-lab1 --template blank
```

### 4. 👾 In your terminal, install the Dependancies:

Navigate into your project directory using your terminal. The path should be point to the project directory create above. Ex. react-native-lab1. Next install the project dependencies using npm. Once the dependencies have loaded open your project on vsCode

```
cd <my-app>

npm install

code .
```

### 5. 👾 Finally, let's launch the project on both web and mobile.

Start the development server with the following:

```
npx expo start
```

This should open up something in your web browser! In the future, you only need to run this command to get your project running.

![https://user-images.githubusercontent.com/26272095/124739226-8622f800-dece-11eb-9006-85771624dff2.png](https://user-images.githubusercontent.com/26272095/124739226-8622f800-dece-11eb-9006-85771624dff2.png)

✅ Click "Run in web browser" and you should see a blank screen with the words "Open up App.js to start working on your app!"

✅ Try scanning the QR code with your Expo app (on Android) or Camera (on iPhone) to see the same screen on your phone.

✅ Here's a reference for all of the files in your new app. Go through each one and check them out so you know what is inside.

- .expo folder = contains configuration information for your machine
- .expo-shared folder = contains info about asset optimization
- **assets folder = contains assets for project (images, icons, fonts, videos)**
- node_modules folder = contains dependencies of project
- .gitignore file = specifies files that Git should ignore
- **App.js file = code to configure our app**
- app.json file = metadata
- babel.config.js file = configuration of how JS code is compiled
- package.json file = manages dependencies
- package-lock.json file = more info about dependencies (stored by npm)
- npm = package manager

> **FYI** from the Expo Docs: "When you run `npx expo start`, Expo CLI starts Metro Bundler, which is an HTTP server that compiles the JavaScript code of our app using Babel and serves it to the Expo app. It also pops up Expo Dev Tools, a graphical interface for Expo CLI."

### 6. 👾 Make your first change.

Open up `App.js` in VSCode.

Change the text on line 8 to whatever you want. You should see it update on your device automatically.

Woohoo! You got your first mobile app running.

# Part 2: Components

✨We're going to learn about React Native components in baby steps. Remember,

- `Components` are building blocks
- `View`, `Text`, and `Style` are React Native Core Components. There are also Community Components (made by React Native community members, that you can find on github or through a quick google search) and Expo-specific Components.
- The style property is passed into a component and dictates the component’s size, color, alignment, spacing, etc..
- Style Classes let us define styles and StyleSheet lets us organize styles, much like CSS!
- Flex properties let us build flexible and well-spaced layouts

## Changing the UI to Yellow:

Our `App.js` component has a styles variable holding the properties of style we want on our `<View>` component. Take a momement and change the background color to yellow

```javascript
import { StatusBar } from "expo-status-bar";
import { StyleSheet, Text, View } from "react-native";

export default function App() {
  return (
    <View style={styles.container}>
      <Text>QuAcK, QuAcK!</Text>
      <StatusBar style="auto" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#fff",
    alignItems: "center",
    justifyContent: "center",
  },
});
```

## If screen is yellow you are done else keep working on this !
