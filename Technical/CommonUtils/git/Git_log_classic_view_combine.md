---
tags: 
  - git
  - workflow
  - best-practices
  - log
alias: [Modern Git, A DOG]
created: 2025-04-05
updated: 2026-01-14
source:
---

# Git Log Classic View Combine

Visualizing the git history effectively is crucial for understanding the project's state. While UI tools exist, the command line `git log` is powerful when combined with specific flags.

## Classic Git Log Parameters

- `--graph`: Draws a text-based graphical representation of the commit history on the left side of the output. This is vital for seeing branches and merges.
- `--oneline`: Condenses each commit to a single line, showing only the abbreviated commit hash and the commit message subject.
- `--decorate`: Shows the names of any branches or tags that point to specific commits (e.g., `HEAD -> main`, `tag: v1.0`).
- `--all`: Displays the history of *all* branches (refs), not just the current one.
- `--stat`: (Optional) Shows a summary of files changed and lines added/deleted for each commit.

## The Ultimate "Combined" View (A DOG)

By combining the flags above, you get a compact, informative visualization of your entire repository history. This is often referred to as "A DOG" (**A**ll **D**ecorate **O**neline **G**raph).

```bash
git log --all --decorate --oneline --graph
```

## Creating a Permanent Alias

Typing this long command every time is tedious. It is highly recommended to add an alias to your global git configuration.

### 1. Simple Alias (`git lg`)

Run the following command in your terminal:

```bash
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

Now you can simply type:

```bash
git lg
```

### 2. The "A DOG" Alias

If you prefer the simpler standard formatting:

```bash
git config --global alias.adog "log --all --decorate --oneline --graph"
```

## Comparison

| Flag | Effect |
| :--- | :--- |
| **No flags** | Standard full output. Good for reading full commit messages. |
| **`--oneline`** | Quick scan of recent history. |
| **`--graph --oneline --all`** | The "Subway Map". Best for understanding branching structure. |
