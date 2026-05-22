# 🦆🦆 Best Practices for Working on a Forked Repo 🦆🦆

> 🔁 Staying Up to Date with the Original Repository (aka Upstream)

🚨🚨 THIS IS A BEST PRACTICE REFERENCE — READ IT THROUGH BEFORE RUNNING COMMANDS 🚨🚨
Also steps will differ on set up, this is specifically because we are working with a fork. Not typically practiced unless you do open-source!

---

## 📌 Scenario

You’ve forked a repo and created a branch to work on a feature.  
But... the original repo (called `upstream`) has changed since you started.  
You now need to **sync your fork** to avoid merge conflicts and make sure your Pull Request (PR) is clean.

---

## 🧭 One-Time Setup — Add the Original Repo as a Remote

Only do this once per fork:

```bash
git remote add upstream https://github.com/ORIGINAL_OWNER/REPO_NAME.git
```

### 🔍 Check that it worked:

```bash
git remote -v
```

You should see:

```
origin    https://github.com/YOUR_USERNAME/REPO_NAME.git (fetch)
upstream  https://github.com/ORIGINAL_OWNER/REPO_NAME.git (fetch)
```

---

## 🦆 Step 1: Sync Your Forked Repo with the Latest Upstream Changes

### 💡 Why?

Over time, the original repo changes. You want to make sure your work builds on the most recent version of the code.

### 🧼 Treat your `main` branch as read-only. Never write code directly on `main`.

---

### ✅ Update your local `main` to match the latest `upstream/main`:
🚧 We typically don't want to do any hard reset, UNLESS we really know what we are doing 🚧 These instructions are specially set up due to the nature of the project, mutiple engineers working on the same files for different features, no hirearcy on who is commiting first 🚧🚧

```bash
git fetch upstream
git checkout main
git reset --hard upstream/main
```

> 📌 `reset --hard` forces your local main to exactly match the latest version of the original repo.  
> ⚠️ Warning: It deletes any local changes or commits on `main` — that’s why we don’t write code on `main`.

---

### 🔼 Push the cleaned-up main to your fork:

```bash
git push origin main --force
```

> This updates your fork on GitHub so it’s fully in sync with the original repo.

---

## 🦆 Step 2: Rebase Your Feature Branch (Optional but Recommended)

Let’s say your branch is called `fix-bug-login`.

```bash
git checkout fix-bug-login
git rebase main
```

> 🧠 This makes it _as if_ you started your work on top of the most recent main.  
> ✨ Clean PRs. Fewer conflicts. Everyone's happy.

---

###  🦆 Push your updated branch:

```bash
git push origin fix-bug-login --force-with-lease
```

> This safely updates your branch on GitHub (only if no one else has pushed to it since).

---

## 🦆 Quick Summary

```bash
# One-time setup
git remote add upstream https://github.com/ORIGINAL_OWNER/REPO_NAME.git

# Regular update process
git fetch upstream
git checkout main
git reset --hard upstream/main
git push origin main --force

# Optional: Update your feature branch
git checkout your-feature-branch
git rebase main
git push origin your-feature-branch --force-with-lease
```

---

## 🚦 Best Practices for this set up; not a common set up on a large code base 🚦

| ✅ Do This                         | 🚫 Avoid This                         |
| ---------------------------------- | ------------------------------------- |
| Work on a new branch from `main`   | Committing directly to `main`         |
| Rebase often to avoid conflicts    | Letting your branch fall behind       |
| Sync your fork before opening a PR | Submitting PRs with stale code        |
| Ask questions before force-pushing | Force-pushing shared or team branches |

---

## 🦆 Need Help?

If you’re unsure about a command or get stuck in a rebase conflict, ask for help. Git is powerful, but it’s okay to make mistakes while learning.
