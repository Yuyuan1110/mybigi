---
tags: 
  - git
  - workflow
  - best-practices
alias: [Modern Git]
created: 2025-04-05
updated:
source:
---

# A Modern Git Workflow

This note outlines a modern approach to using Git that prioritizes clarity, a clean project history, and the use of newer, more intuitive commands. This workflow helps avoid common pitfalls and makes collaboration easier.

The core philosophies are:
- **Clarity over brevity**: Use commands that are explicit and less ambiguous.
- **Clean, linear history**: Use `rebase` to avoid messy "merge bubbles" in the project history.
- **Intentional commits**: Craft meaningful commits with detailed messages.

See also: [[Git_Commit_Message_convention]]

---

## Core Command Replacements

- **Use `switch` and `restore`**, not `checkout`. `switch` is for changing branches (`git switch -c <branch>`) and `restore` is for discarding file changes (`git restore <file>`).
- **Use `git commit`**, not `git commit -m`. This encourages writing detailed commit messages in an editor, following best practices.

---

## The Modern Feature Branch Workflow

### Step 1: Configure Your Remotes (One-Time Setup)

In a typical fork-based workflow, you have two remotes:
- **`origin`**: Your personal fork of the repository.
- **`upstream`**: The main, official repository.

```bash
# Check your current remotes
git remote -v

# If you don't have an upstream, add it. (Get the URL from the main project page)
git remote add upstream https://github.com/official-project/project.git
```

### Step 2: Sync Your Local `main` Branch

Before starting any new work, always sync your local `main` branch with the `upstream` repository.

```bash
# Switch to your main branch
git switch main

# Fetch the latest changes from the upstream repository
git fetch upstream

# Reset your local main branch to match the upstream main branch exactly
git reset --hard upstream/main

# (Optional but recommended) Push the updated main to your fork
git push origin main --force
```

### Step 3: Start a New Feature Branch

Create your new feature branch from your now up-to-date local `main` branch.

```bash
git switch -c my-new-feature
```

### Step 4: Make and Commit Changes

Work on your code and make small, atomic commits. Don't worry about making them perfect yet; you will clean them up later.

```bash
git add <files>
git commit
```

### Step 5: Clean Up Your History with Interactive Rebase

**This is the most important step for creating a clean pull request. Only do this on a branch that you have not shared with others yet.**

Before you push your work, you should clean up your local commits. Interactive rebase allows you to edit, reword, combine, and reorder your commits into a logical sequence.

```bash
# First, make sure your branch is up-to-date with main
git fetch upstream
git rebase upstream/main

# Now, start an interactive rebase on top of the main branch
git rebase -i upstream/main
```

This command will open an editor with a list of your commits. You can use the following commands:
- **`p`, `pick`**: Use the commit as-is.
- **`r`, `reword`**: Keep the commit's changes, but edit the commit message.
- **`e`, `edit`**: Pause the rebase at this commit to make changes (e.g., split it into smaller commits).
- **`s`, `squash`**: Combine this commit with the one above it and merge the commit messages.
- **`f`, `fixup`**: Like `squash`, but discard this commit's message entirely.

Follow the on-screen instructions to clean up your history until it tells a clear, logical story.

### Step 6: Share Your Work

Once your history is clean and you have rebased against the latest `main`, you can push your branch to your fork (`origin`).

```bash
# If this is the first time pushing this branch:
git push -u origin my-new-feature

# If you have rebased a branch that was already pushed, you must force push:
# WARNING: Be very careful with this command.
git push --force-with-lease origin my-new-feature
```

After pushing, you can open a Pull Request. The commit history will be clean and easy for reviewers to follow.