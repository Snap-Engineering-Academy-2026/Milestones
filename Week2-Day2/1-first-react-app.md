# First React App

Time to create your first web app with React!

## 1. Starter Code with Vite

You're going to be using Vite to create this app, which is a build tool that will create some starter code for you.

Follow [the instructions in the documentation](https://vite.dev/guide/) until you get to something that looks like the picture below:

<table><tr><td>
<details>
  <summary>Training Wheels 1</summary>
  
  <br/>
  
  One of the skills of reading documentation is learning what to pay attention to and what to ignore. While you can read the stuff at the top, the instructions we actually want are a few sections down called "[Scaffolding Your First Vite Project](https://vite.dev/guide/#scaffolding-your-first-vite-project)"
  
  From there, we can see some terminal commands like `npm create vite@latest`. That command will create a project folder with a bunch of files in it. _You could just open terminal and run that command, but it's also worth considering what folder you run that command from. You want to be able to find it again!_
  
  One possible organization option is to create a folder somewhere for all of your SEA work, and then create all of the project folders in there. You could do this by opening Terminal, running `mkdir SEA-code` (or whatever you want to name it) then `cd SEA-code`. Now you're inside your SEA folder, so when you run `npm create vite@latest` it will create the project inside your SEA folder.
  
  <br/>

</details>
</td></tr></table>

  After running `npm create ...`, you'll have to give your project a name and choose some options. Choose these options: `React`, then `JavaScript` (not JavaScript + SWC).

<table><tr><td>
<details>
  <summary>Training Wheels 2</summary>
  
  <br/>
  
  After you're created the project files with Vite, you need to install the dependencies and run the code!

  Vite gives you the commands:
  ```
  cd <project-name>
  npm install
  npm run dev
  ```
  
  - `cd <project-name>` will move your terminal into the project folder Vite just created.  
  - `npm install` is a Node Package Manager command to install of the dependencies (or packages) that this starter code needs to run.  
  - `npm run dev` looks like a Node Package Manager command, but it's actually a disguised Vite command that tells Vite to start the web app in "developer mode."
  
  Once you're there, click on the link, probably http://localhost:5173/, to open the website.
  
  <br/>

</details>
</td></tr></table>

<img width="1126" alt="image" src="https://github.com/user-attachments/assets/5bf5f745-beca-405f-9ea2-d21ce741edb2" />
  
<br/>

<br/>

<br/>

## 2. Editing Code

View the code in VS Code

1. In your terminal, stop Vite with by pressing `Control+C` on your keyboard. (`Control+C` is commonly used to stop/exit a process running in your terminal).
2. Next, we'll use terminal to open VS Code. You already know that `code` will open VS Code, but we want to view the code in this folder specifically, so an even better command would be `code .` _The `.` is shorthand for the "current directory" aka the folder your terminal is at._
3. Look around the code!
4. Open `App.jsx` and discuss what you see with a partner.
5. Make a minor change to the code in `App.jsx`. Did the website change? If not, can you figure out why?

> [!IMPORTANT]
> Do not move on until you can edit `App.jsx` and see that new change on the website. 
  
<table><tr><td>
<details>
  <summary>Training Wheels</summary>
  
  <br/>
  
  To see our code changes on the website, we need to make sure Vite is running! We stopped it earlier with `Control+C`.
  
  Open Terminal again. I recommend using VS Code's built-in terminal, because it will automatically set you up in the correct folder. To do this, go to the very top of your screen with VS Code open and choose Terminal > New Terminal

  <img width="765" alt="image" src="https://github.com/user-attachments/assets/3db2d2d7-3ae3-40cd-a90a-f836ba91299f" />

  Now, you can run the same command from earlier `npm run dev`
  
  <img width="1195" alt="image" src="https://github.com/user-attachments/assets/d459b68a-660b-4b89-8672-9e670e7ec0ac" />

  This restarts the web server process using what's called "development mode." _It's called "development mode" because this is the mode used to "develop" the code, as opposed to "production mode" which is used when the website is hosted publicly._
  
  Now that the process is running again:
   - Make a change to the code
   - **Save the file with `Command+S`!** (or lookup the setting to make VSCode autosave) 
  
  You'll be able to see the code changes on the website!
  
  <br/>

</details>
</td></tr></table>

<img width="1237" alt="image" src="https://github.com/user-attachments/assets/e41710fb-2e73-4619-8f22-ab287dfeb921" />

<br/>

<br/>

<br/>

## 3. Components and a Component Library

One of the most helpful "features" of React is the ability to decompose our code using "Components." _In the same way that functions help us organize and reduce repitition in normal code, components help us do the same in JSX, or React code._

There are also "Component Libraries" which are libraries of components that come with prewritten CSS and JavaScript. _In the same way that you should almost always use a library for a sorting algorithm instead of writing your own, you should also usually use component libraries for buttons, menu bars, search boxes, and other common website elements instead of writing your own._

For SEA, we'll show you how to use a popular component library called Material UI.

### Material UI Example

1. To use Material UI, you need to install it. Use this terminal command (copied straight from the [Material UI documentation](https://mui.com/material-ui/))
```bash
npm install @mui/material @emotion/react @emotion/styled
```
2. Next, replace all of your code in `App.jsx` with this custom example. (Open the spoiler to see the code to copy)
<table><tr><td>
<details>
  <summary>App.jsx</summary>
  
```jsx
import Button from "@mui/material/Button";
import Typography from "@mui/material/Typography";
import Container from "@mui/material/Container";
import './App.css'
// import characters from './protagonists.json'

function App() {
  return (
    <>
      <Container maxWidth="md" sx={{ mb: 4 }}>
        <Typography
          variant="h2"
          align="center"
          color="text.primary"
          sx={{ py: 2 }}
        >
          CSS Mystery
        </Typography>
        <Typography
          variant="h5"
          align="center"
          color="text.secondary"
          sx={{ mx: 10 }}
        >
          Why isn't the CSS working?
        </Typography>
      </Container>

      <Container maxWidth="lg">
        <Button
          variant="contained"
          // I'm trying to use custom CSS defined in the file App.css,
          // but it isn't working. Why, and how can I fix it?
          className="characterButton"
        >
          Red Button?
        </Button>
      </Container>
    </>
  )
}

export default App
```
  
  <br/>

</details>
</td></tr></table>

3. Also replace all of your code in `App.css` with this
<table><tr><td>
<details>
  <summary>App.css</summary>
  
```css
html body {
  display: block;
  place-items: normal;
}

.characterButton {
  /* Why doesn't this work? (See line #39 in App.js for where this class is applied) */
  background-color: red;
}
```
  
  <br/>

</details>
</td></tr></table>

When you're done, your page should look like this:

<img width="1552" alt="image" src="https://github.com/user-attachments/assets/877808ad-757b-4df0-a380-126c3fe48cd8" />

<br/>

<br/>

<br/>

## 4. CSS Mystery

Now, solve the CSS mystery! 

In `App.css`, there's some CSS that should be making the button red, but it isn't working.

Dive into the issue and try to figure it out. Why is the button blue instead of red?

> [!IMPORTANT]
> Do not move on until you have figured out how to make the button red **and** have some understanding of why the initial CSS didn't work. 

<table><tr><td>
<details>
  <summary>Hint</summary>
  
  <br/>
  
  When you open the Chrome developer tools panel (look up how if you're unfamiliar) there is a tool that allows you to inspect the CSS that is being applied to elements on a page, and it also tells you where that CSS came from. 

  Also, while you can use `!important` in the CSS to change the color to red, there is a deeper problem that we want you to solve.
  
  <br/>

</details>
</td></tr></table>

<img width="1237" alt="image" src="https://github.com/user-attachments/assets/a6d9eaf4-409d-4cff-8b1c-2cd5b8674c96" />

<br/>

<br/>

<br/>

## Fin

Finished? Try to figure out how to back up your project to Github!

