# Final Project Starter

https://github.com/Snap-Engineering-Academy-2025/SnapChatStarterForkable

This will be the starter code for your final project! But first, we're going to spend a day making improvements to it. We'll use pull requests to manage this, and for that you'll need to be on your own branch. You can work in pairs or on your own.

### Create your branch

After cloning this repo to your computer, **make a new branch** with your name! All of your changes need to be on this branch.

The `git checkout` command move you to a different branch, and adding the `-b` flag will create a new branch before moving you 

```bash
git checkout -b <new-branch-name>
```

## Milestone 1 - Improve the starter code

Launch the app and explore the starter code. Note any errors / warnings that you find, along with any other small bugs. Once you think you've seen all the different parts of the app, choose something **small** to fix or add to the starter code!

Once you've chosen your **small** fix/addition, "claim" it by creating an issue on the starter code repo. Make sure to select the Snap25 template. Make sure to practice good documentation skills. You can always collaborate/pair-program with others if you both want to work on the same thing!

When you've finished your small fix, check out the steps below.

## Make sure you Keep Your Fork Updated
Remember when we set up the project we added a remote called 'upstream'? When you fork a repository, you create a copy of the original repository (upstream) in your own GitHub account. Over time, the original repository might get updated with new commits, and you'll want to incorporate those changes into your fork to keep it up-to-date. Here’s how you can do that:

### Fetch Upstream Changes

Fetching means downloading the commits from the remote repository (upstream) but not merging them into your local branch automatically. This is useful to see what changes have been made in the original repository without altering your working branch immediately.
```js
$ git fetch upstream
```
What it does: Downloads all the changes from the upstream repository but does not apply them to your branch immediately.
Why it’s useful: Allows you to review changes and decide how and when to integrate them.

### Merge Upstream Changes into Your Branch
Once you have fetched the changes, you can merge them into your current branch. This way, you have control over how the changes are applied and can resolve any conflicts that might arise.
```js
$ git checkout your-branch-name
$ git merge upstream/main
```
What it does: Merges the fetched changes from the upstream repository’s main branch into your current branch.
Why it’s useful: Allows you to carefully integrate changes and resolve conflicts manually if they arise.

### Resolving Merge Conflicts
When you merge changes, sometimes the same lines of code might have been altered both in your branch and the upstream branch. These are called conflicts. You’ll need to resolve these conflicts manually by deciding which changes to keep.

#### Why Not `git pull` Directly?
`git pull` is essentially a shortcut that combines git fetch and git merge:

```js
$ git pull upstream main

```
What it does: Fetches changes from the upstream repository and merges them into your current branch in one step.
Why it might be problematic:
If there are conflicts, they’ll need to be resolved immediately, which can be confusing for beginners.
It can make it harder to review the changes before they’re merged into your branch.


## 4. Create your pull request
Once you are ready to push your code to the starter code, you will begin the process of creating a Pull Request 

<details>
<summary>OPEN ME! Steps Inside</summary>

### A - Add and Commit your changes locally
  
```bash
git add .
git commit -m "commit message"
```
or
```bash
git commit -am "commit message"
```

### B - Push your changes

Pushing your changes from here is less straightforward than you think. Try this command:

```bash
git push
```

We get this message:

![Screen Shot 2024-07-23 at 9 54 38 AM](https://github.com/user-attachments/assets/d592b7ea-cb64-4a64-838d-6c0c06ab5e3e)

This is cuz git doesn't know if we want to push our changes to the `origin` repo or the `upstream` repo. But which one is which? Run this command to see:

```bash
git remote -v
```

That command will list the URLs for the "remote" repos connected to this repository, and we have two: `origin` and `upstream`. 

Now, look at the error message we got earlier and the command it suggests. Once you think you know what it means, run it!

From now on, we can simply use `git push` to push our changes, but for the first time we had to do that extra bit of setup.

<br>

### C - View and starting creating your pull request on Github
1. Navigate to your forked repository on GitHub.
Click on the "Compare & pull request" button: This usually appears after you push your changes to GitHub.

![Screen Shot 2024-07-23 at 10 03 32 AM](https://github.com/user-attachments/assets/4de7b2a5-9f54-45fa-b578-5288076aab0e)

<br></br>
when your Pull Request Opens make sure you are checking that you are comparing your branch to the main branch of the classroom repository 

![image](https://github.com/user-attachments/assets/4ec69c64-49ed-4f55-a08e-97669d0ae80e)

### D - Describe your pull request
In your pull request, please be specific about what updates you have added. The header should summarize the main fixes that your edits address and your comment
should include specific details of exactly what was changed. Please include screenshots of the edited screen before and after your changes. Here is a great 
example from Felicia.

![image](https://github.com/user-attachments/assets/9b2df100-eea6-4500-8d24-8c26cd10c916)


### F - View your created pull request

![image](https://github.com/user-attachments/assets/ce0aba1d-7086-497b-978c-08288ac9e307)

</details>

<br/>

<br/>

## 5. Review and Merge your changes

After you've created a pull request, you won't be able to merge the changes until your PR gets "approved." This is common practice, and we did this back in week 1! In this case, you'll need to ask an instructor to review and approve your changes. 

Once your changes are approved, you'll be able to merge the changes in to the repo. 

You can start working on another bug/addition now, just make sure to make a new branch for it!

<br/>

<br/>

