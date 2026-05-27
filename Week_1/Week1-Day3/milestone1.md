# Partner Bug Fix Task: Change the Button Color

## Objective

You will work on a **peer’s repository**, not your own. Your task is to **fix the same bug**: change the color of a button. This exercise will simulate contributing to someone else's codebase via GitHub.

---

## Step 1: Get Assigned a Partner's Repository

1. Get your partner's GitHub repository URL.
2. **Do not clone your own repo.** You will be working on your partner's project.

---

## Step 2: Create a GitHub Issue on Their Repo

1. Go to your partner's GitHub repo.
2. Click on the `Issues` tab.
3. Click `New Issue`.
4. Title it: `Change Button Color`
5. Description:

   ```md
   The current button color does not meet our design requirements.  
   ✅ Task: Change the button background color from `[#currentColor]` to `[#desiredColor]`.  
   This improves the accessibility and UI consistency.

   Please assign this issue to me.
   ```

# Step 3. Fork the repo on GitHub first using the "Fork" button on the top right

### Then clone your fork locally

git clone https://github.com/your-username/their-repo-name.git

## Step 4. Create a feature branch

```
git checkout -b change-button-color
```

## Step 5: Make the Code Change

Locate the button in the code (likely in a .jsx, .tsx, .js, or .css file).

Change the background color to the new one specified in the issue.

Save and test your changes locally.

```
git add <file_name>
```

## Step 6 :Commit the changes

```
git commit -m "fix: change button color to [#desiredColor]"
```

## 7. Step 7: Push and Create Pull Request

```
git push origin change-button-color
```

Go to your forked repo on GitHub.

You should see a prompt to Create a Pull Request.

Set the base repo to your partner’s original repo.

Add this message:

This PR fixes Issue #[issue-number]: Changes the button color to improve UI consistency and accessibility.
Submit the pull request.their-repo-name
