# Copying Github Repo Lab Template:

1. Start from the parent directory of your choosing (like `~` or `SEA-code`) and create a new blank expo project:
```
npx create-expo-app@latest spotify-navigation-lab --template blank
```  

2. Enter the new project folder with:
```
cd spotify-navigation-lab
```

3. Start the project and test to make sure it works!

```
npx expo start
```

<img width="517" alt="image" src="https://github.com/user-attachments/assets/a46a904e-3bcd-4676-ba46-7963eeec2a88" />

<br/>

<br/>

<br/>

4. Next, we're going to grab some starter code. There are a number of commands to run for this step, with brief explanations below each one.  

```
gh repo clone Snap-Engineering-Academy-2025/starter-spotify-navigation-lab temp-spotify-starter-code
```
_Download a "temp" copy of a github repository with the files we want. We don't want all of the files though, just some specific ones._
```
cp -rn temp-spotify-starter-code/assets/* ./assets/
```
_Copy the files from the assets folder_
```
cp -rn temp-spotify-starter-code/components ./components
```
```
cp -rn temp-spotify-starter-code/screens ./screens
```
```
cp -rn temp-spotify-starter-code/utils ./utils
```
_Copy the `components`, `screens`, and `utils` folders_
```
cp temp-spotify-starter-code/App.js ./App.js
```
_Replace the blank `App.js` with the temp code's version._
```
npx expo install expo-auth-session expo-crypto axios
```
_Install the dependencies needed to run the new code._
```
rm -rf temp-spotify-starter-code
```
_Delete the rest of the "temp" code_

<br/>

<br/>

5. Start the app again! You should get an error (Yes, you are supposed to get an error, either “Console Error” or “AuthRequest Error”)

```
npx expo start
```

<img width="517" alt="image" src="https://github.com/user-attachments/assets/c0e5852d-20eb-4919-84cf-f5c78bc07d23" />

<br/>

<br/>

<br/>

## Fin

Yay!

