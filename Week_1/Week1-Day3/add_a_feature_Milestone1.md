# Partner Bug Fix Task: Reverse Search

## Objective

You will work on a **peer’s repository**, not your own. Your task is to **add another search bar**: The goal is to exclude letters typed in by the user. This exercise will simulate contributing to someone else's codebase via GitHub.

---

## Step 1: Get Assigned a Partner's Repository

1. Get your partner's GitHub repository URL.
2. **Do not clone your own repo.** You will be working on your partner's project.

---

## Step 2: Create a GitHub Issue on Their Repo

1. Go to your partner's GitHub repo.
2. Click on the `Issues` tab.
3. Click `New Issue`.
4. Title it: `Feature_Reverse_Search`
5. Description:

   ```md
   The current catalogy is missing a reverse search feature  
   ✅ Feature: Add a second search bar to allow users to exclude letters instead of includes.  
   This improves the accessibility and UI consistency.
   ```

# Step 3. Fork the repo on GitHub first using the "Fork" button on the top right

### Then clone your fork locally

git clone https://github.com/your-username/their-repo-name.git

## Step 4. Create a feature branch

```
git checkout -b feature-reverse-search
```

## Step 5: Make the Code Change

Add the neccessary code to make the changes.

Save and test your changes locally.

```
git add <file_name>
```

## Step 6 :Commit the changes

```
git commit -m "feat: added reverse search"
```

## 7. Step 7: Push and Create Pull Request

```
git push origin feature-reverse-search
```

Go to your forked repo on GitHub.

You should see a prompt to Create a Pull Request.

Set the base repo to your partner’s original repo.

Add a message:

- include screenshots or gifs of your feature working!
