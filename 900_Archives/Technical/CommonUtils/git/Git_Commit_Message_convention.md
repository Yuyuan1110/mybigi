# Git Commit Message Convention

Writing a good commit message is very important. A good commit message helps maintainers (and your future self) easily understand the reason for a change and track the history of the codebase. A bad commit message can make this process difficult or impossible.

This note records a set of conventions to follow for creating clear and structured commit messages.

**Reference Articles:**
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
- [AngularJS Git Commit Message Conventions](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit)
- [How to Write a Git Commit Message](https://cbea.ms/git-commit/)

## The 7 Rules of a Great Commit Message

1.  **Separate subject from body with a blank line.**
2.  **Limit the subject line to 50 characters.**
3.  **Capitalize the subject line.**
4.  **Do not end the subject line with a period.**
5.  **Use the imperative mood in the subject line.** (e.g., `Add feature` not `Added feature` or `Adds feature`)
6.  **Wrap the body at 72 characters.**
7.  **Use the body to explain *what* and *why* vs. *how*.** The code itself explains *how*. The commit message should explain the intent and the reasoning behind the change.

---

## Commit Message Structure

A conventional commit message follows this structure:

```
<type>[optional scope]: <subject>

[optional body]

[optional footer]
```

### Type

The type is mandatory and describes the category of the change. The most common types are:

- **`feat`**: A new feature for the user.
- **`fix`**: A bug fix for the user.
- **`docs`**: Changes to documentation only.
- **`style`**: Code style changes that do not affect meaning (e.g., white-space, formatting, missing semi-colons).
- **`refactor`**: A code change that neither fixes a bug nor adds a feature.
- **`perf`**: A code change that improves performance.
- **`test`**: Adding missing tests or correcting existing tests.
- **`chore`**: Changes to the build process or auxiliary tools and libraries such as documentation generation. `chore` is often used for routine maintenance.
- **`revert`**: Reverts a previous commit.

### Scope (Optional)

The scope provides additional contextual information. It's a noun describing the section of the codebase affected by the change (e.g., `auth`, `api`, `ui`).

**Example:** `feat(auth): Add password reset functionality`

### Subject

The subject contains a concise description of the change.

- **Use the imperative mood.** Write as if you are giving a command. (e.g., `Fix bug`, `Add feature`)
- **Keep it under 50 characters.** This ensures it is readable on GitHub and in various Git tools.
- **Capitalize the first letter.**
- **Do not end with a period.**

**Good Subject Examples:**
- `feat: Allow users to upload avatars`
- `fix: Correctly calculate tax in shopping cart`
- `docs: Update installation instructions`

### Body (Optional)

The body is used to explain the *what* and *why* of the change, not the *how*. It should provide context that cannot be easily understood from the code itself.

- Explain the problem that the change solves.
- Describe the reasoning behind your solution.
- Separate paragraphs with a blank line.
- Wrap lines at 72 characters.

**Example Body:**

```
The previous implementation was causing a race condition when multiple users tried to update their profile simultaneously.

This change introduces a locking mechanism to ensure that only one update can be processed at a time, preventing data corruption.
```

### Footer (Optional)

The footer is used to reference tracking IDs from issue trackers (e.g., Jira, GitHub Issues) or to denote breaking changes.

- **Breaking Change:** A `BREAKING CHANGE:` footer indicates that the commit introduces a significant change that requires consumers of the code to make modifications.
- **Issue Tracking:** You can reference issues like `Fixes #123` or `Closes #456`.

**Example Footer:**

```
BREAKING CHANGE: The `getUser` API endpoint now returns an object instead of a string.

Fixes: #123, #456
```
