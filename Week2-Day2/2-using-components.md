## 0. Backup with git

Before you proceed, you should back up your code to Github!

Start by going to Github and creating a new repository (make the owner "Snap Engineering Academy 2025"). See if you can figure it out from there!

<table><tr><td>
<details>
  <summary>Training Wheels</summary>
  
  <br/>
  
  Once you've created a new repository, you should see a page like this:

  <img width="1290" alt="image" src="https://github.com/user-attachments/assets/08ae0600-821a-4cfc-9c42-356552af791f" />

  The commands under the "…or create a new repository on the command line" section are the best place to start! Here's what they do.

  - `echo "# baker-sea-react-example" >> README.md`
    - Adds a title to the `README.md` file. Your starter code already has a README, so you could skip this.
  - `git init`
    - Start using Git in this folder.
  - `git add README.md`
    - Tells Git to keep track of the `README.md` file.
  - `git commit -m "first commit"`
    - Commits the current version of the file with a message.
  - `git branch -M main`
    - Names the main branch of the project "main".
  - `git remote add origin ...`
    - Connects your project to a GitHub repository.
  - `git push -u origin main`
    - "Pushes" or uploads your project to GitHub and sets up the connection for future updates.
  
  If you go look at your github repository now, you should see a README.md file, but everything else is missing!

  If you type `git status` you'll see there that all of the other files are red and "untracked"

  To track and back up all the other files, do these commands:

  - `git add .`
    - Tells Git to keep track of all of the files in the currect directory.
  - `git status`
    - Not necessary, but now you see all the files are green and "to be committed"
  - `git commit -m "Added remaining files of starter code"`
    - Commits the current version all of the files with the message "Added remaining files of starter code." Try to get in the habit of writing descriptive commit messages. When you need to go back and find an old version of a file, having descriptive messages makes it way easier!
  - `git push`
    - Pushes your new commit with all the new files to Github.
   
  Go back to Github again and you should see all of the project files now!
  
  <br/>

</details>
</td></tr></table>

<br/>

<br/>

<br/>

# Using Components

## 1. Card Component

Go to the [Material UI documentation for the Card component](https://mui.com/material-ui/react-card/), copy one of the examples, and get it working in your code. _Tip: read through the example carefully and try to copy only what you need. Copying the whole file is unlikely to work, and just bad practice._

<table><tr><td>
<details>
  <summary>Training Wheels 1</summary>
  
  <br/>
  
  This is another exercise in what to pay attention to and what to ignore. I ended up using [this card](https://mui.com/material-ui/react-card/#media) with the picture of a lizard.
  
  I start by copying all of the JSX code from the example `<Card sx={{ maxWidth: 345 }}> ... </Card>`. I paste that into my code inside the `Container` component, replacing the `Button` code. So it looks like this:

```jsx
<Container maxWidth="lg">
  <Card sx={{ maxWidth: 345 }}>
    ...
  </Card>
</Container>
```

  When I save and look at the output. I get a blank screen. 
  
  I check for errors using Inspect and going to the Console tab:

  <img width="1266" alt="image" src="https://github.com/user-attachments/assets/80161bd9-51ea-464f-9923-f2edd65fc6cd" />

  The most important error message is almost always the first one (at the top). Look it up and see if you can figure out what's wrong! 
  
  <br/>

</details>
</td></tr></table>

<table><tr><td>
<details>
  <summary>Training Wheels 2</summary>
  
  <br/>
  
  That error message shows up because we just copied code that uses the `Card` component from Material UI, but we haven't imported it. Material UI only loads exactly what we need for performance reasons. We have to import `Card` and the other components at the top of the file. We can just copy the imports from the example code!

```jsx
import Card from "@mui/material/Card";
import CardActions from "@mui/material/CardActions";
import CardContent from "@mui/material/CardContent";
import CardMedia from "@mui/material/CardMedia";
```

  This should make almost everything work, but it's likely the image in the card won't work. This is the code to reference the image: `image="/static/images/cards/contemplative-reptile.jpg"`

  That is looking for an image file "locally" in a specific folder, which we don't have. As a quick fix, we can just use an image URL instead: `image="https://mui.com/static/images/cards/contemplative-reptile.jpg"`

  At this point, when you save and look at your page, everything should be working!
  
  <br/>

</details>
</td></tr></table>

<img width="1266" alt="image" src="https://github.com/user-attachments/assets/cced2d18-7317-46de-9965-a32ce47e1238" />

<br/>

<br/>

## 2. Grid Component

Go to the Material UI documentation for the Grid component, then use the examples to make a "grid" of at least two cards. _No documentation link this time, find it yourself!_

<table><tr><td>
<details>
  <summary>Training Wheels</summary>
  
  <br/>
  
  The first part of the process is the same as for the Card component, but the documentation page for the Grid component is more obtuse. 
  
  The general idea looks like this:

```jsx
<Grid container spacing={4}>
  <Grid>
    ... first grid item ...
  </Grid>

  <Grid>
    ... second grid item ...
  </Grid>
</Grid>
```

  I used the Grid props `container` and `spacing={4}` in this example. You can read the documentation or try removing each of them separately to get an idea of what they do.
  
  <br/>

</details>
</td></tr></table>

<img width="1266" alt="image" src="https://github.com/user-attachments/assets/b9b33bc3-096b-482a-9061-cb55efdbe1e2" />

<br/>

<br/>

## 3. Customizing

Display a few pieces of data from your project website using the Material UI Card and Grid. You can recreate something from your website or make a totally new display.

<img width="1358" alt="Screenshot 2025-06-13 at 2 07 41 PM" src="https://github.com/user-attachments/assets/9761b143-6cf5-4fa9-ba6f-78fe25966016" />

<br/>

<br/>
