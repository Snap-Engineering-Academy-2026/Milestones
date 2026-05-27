# Combining Spotify Navigation Lab and Triviachat Lab

In this lab, we're going to be combining the two labs we worked on last week. Instead of a list of songs that can be pressed to view song details, you'll end up with a list of conversations/chatbots that can be pressed to open up that conversation!

## Milestone 1 - Setup

Follow the steps in the readme here:

https://github.com/Snap-Engineering-Academy-2025/combine-spotify-triviachat

## Milestone 2 - Adding your own Chatbot

Add your TriviaChat Chatbot from last week's lab to this new repo so that the list of chatbots now shows 3 chatbot conversations. Make sure you can click on your triviachatbot and play it!

1. Add a new file in the components folder, and paste your code into it!
2. Look at `ChatScreen.js` and follow the two existing examples to add your TriviaChat to the list.

## Milestone 3 - Add someone else's chatbot

Add a classmate's chatbot to your list of chatbot conversations!

They should be able to send you their whole file and you can add it just like you added your own.

## Milestone 4 - Give your chatbots a mini-makeover!

If you haven't already, give your and your classmate's chatbots cool names, a custom avatar / profile photo, and so on!

Do not delete the starter chat bots, we will be working with them later in the project 

## Milestone 5 - Code cleanup

When we adapted the Spotify lab to work for chatbot, we tweaked some things, but we also took some shortcuts. Some of this was laziness (:shrug:) we also wanted you all to see how we reused so much of the code from the Spotify lab. However, we didn’t “fully transition” and rename everything.

It's your job to clean it up:
 - Some files aren’t used anymore.
 - Some files are still used but need to be refactored, so that the variable/prop names line up better with “chatbots” vs “songs / spotify”
 - `Song.js` could use a lot of improvements. Rename it, and change it so it only shows information relevant to your chatbots (for example, chatbots don't need a duration)
 - Document the fixes you make to share with others!
