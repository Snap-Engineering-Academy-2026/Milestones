# Checkpoint 2: Connecting your app to Spotify 

## Get the access identification stuff to get data from your Spotify account!
1. Log into [Spotify for Developers](https://developer.spotify.com/) and navigate to your developer dashboard. *Create a spotify account with a personal email if you don't have one already.*
2. Click `Create App`
3. Give your app a name and description
4. For the redirect URI, input the expo URL of your project (the one that is outputted after running `yarn expo start` 
![image](https://github.com/user-attachments/assets/87833872-4953-43ab-afb3-4d2b910ddb52)

5. Save your app
6. This should redirect you to a status page for your app that looks like this: 
![image](https://github.com/user-attachments/assets/68cae504-3497-4d2b-a0c0-a29c27c8b834)

7. Click `Settings` to see your `Client ID`.
8. Copy this value and navigate to your `env.js` file
9. Paste this value into `CLIENT_ID` and paste your redirect URI to `REDIRECT_URI`

<img width="1156" alt="Screenshot 2025-07-08 at 12 01 11 PM" src="https://github.com/user-attachments/assets/7c7cca54-03f3-4fbf-84aa-b58b99c3d74a" />

</br>

</br>

## Reload the app and check out your songs!

1. The error should go away, and you will see a green “Connect with Spotify” button.
2. Click the button and sign in to check out your top tracks. *If you just created an account it'll show some Kanye songs by default*

</br>

<p align="middle">
  <img src="https://github.com/Snap-Engineering-Academy-2024/Milestones/assets/7607483/fbafffe3-8f50-4297-8f83-8e4d06cf610d" width="300" hspace="20"/>
  <img src="https://github.com/Snap-Engineering-Academy-2024/Milestones/assets/7607483/31616143-acfb-4504-86fe-d9fcd7b1165a" width="300" hspace="20"/> 
</p>

