# Working with Git Branches: Rename, Switch, Commit, and Delete (with Command Output)

This guide demonstrates the process of creating, renaming, working on, and safely (or forcefully) deleting branches in
Git, including the actual output you would see at each step.

---

## 1. Create a New Branch

```bash
git branch bugfix
```

- Creates a new branch called `bugfix` at your current commit.

---

## 2. List All Branches

```bash
git branch
```

**Output:**

```
* bugfix
  master
```

- The `*` shows your current branch is `bugfix`.

---

## 3. Switch to the Branch

```bash
git switch bugfix
```

- Now you’re working on `bugfix`.

---

## 4. Rename the Branch to Something More Descriptive

```bash
git branch -m bugfix bugfix/signup-form
```

- `-m` renames `bugfix` to `bugfix/signup-form` (a more descriptive name).

---

## 5. Edit a File and Stage the Change

```bash
vi audience.txt   # (edit: add or delete some content)
git add audience.txt
```

- Makes and stages changes for commit.

---

## 6. Commit Your Changes

```bash
git commit -m "Fix the bug that prevented the users from signing up."
```

- Records your changes on `bugfix/signup-form`.

---

## 7. View the Log (Current Branch)

```bash
git log --oneline
```

**Output:**

```
05d3fdc (HEAD -> bugfix/signup-form) Fix the bug that prevented the users from signing up.
a642e12 (master) Add header to all pages.
50db987 Include the first section in TOC.
555b62e Include the note about committing after staging the changes.
91f7d40 Explain various ways to stage changes.
edb3594 First draft of staging changes.
24e86ee Add command line and GUI tools to the objectives.
36cd6db Include the command prompt in code sample.
9b6ebfd Add a header to the page about initializing a repo.
fa1b75e Include the warning about removing .git directory.
dad47ed Write the first draft of initializing a repo.
fb0d184 Define the audience.
1ebb7a7 Define the objectives.
ca49180 Initial commit.
```

- Your new commit is at the top of this branch.

---

## 8. Switch Back to Master

```bash
git switch master
```

- You’re now back on `master`.

---

## 9. View the Log Across All Branches

```bash
git log --oneline --all
```

**Output:**

```
05d3fdc (bugfix/signup-form) Fix the bug that prevented the users from signing up.
a642e12 (HEAD -> master) Add header to all pages.
50db987 Include the first section in TOC.
555b62e Include the note about committing after staging the changes.
91f7d40 Explain various ways to stage changes.
edb3594 First draft of staging changes.
24e86ee Add command line and GUI tools to the objectives.
36cd6db Include the command prompt in code sample.
9b6ebfd Add a header to the page about initializing a repo.
fa1b75e Include the warning about removing .git directory.
dad47ed Write the first draft of initializing a repo.
fb0d184 Define the audience.
1ebb7a7 Define the objectives.
ca49180 Initial commit.
```

- `HEAD -> master` shows you’re on master, but the bugfix branch’s commit is **not** merged.

---

## 10. Delete the Feature Branch

### Try to Delete Normally:

```bash
git branch -d bugfix/signup-form
```

**Output:**

```
error: The branch 'bugfix/signup-form' is not fully merged.
If you are sure you want to delete it, run 'git branch -D bugfix/signup-form'.
```

- Git warns you: Branch has commits not in master!

---

### Force Delete the Branch:

```bash
git branch -D bugfix/signup-form
```

**Output:**

```
Deleted branch bugfix/signup-form (was 05d3fdc).
```

- Branch is deleted, even though it wasn’t merged.

---

## Summary Table

| Command                                 | Description                    | Example Output (if any) |
|-----------------------------------------|--------------------------------|-------------------------|
| git branch bugfix                       | Create new branch              |                         |
| git branch                              | List branches                  | * bugfix<br>  master    |
| git switch bugfix                       | Switch to branch               |                         |
| git branch -m bugfix bugfix/signup-form | Rename branch                  |                         |
| git add audience.txt                    | Stage changes                  |                         |
| git commit -m "..."                     | Commit changes                 |                         |
| git log --oneline                       | View commit log (branch)       | see above               |
| git switch master                       | Switch to master               |                         |
| git log --oneline --all                 | View commit log (all branches) | see above               |
| git branch -d bugfix/signup-form        | Delete branch (safe)           | error: not fully merged |
| git branch -D bugfix/signup-form        | Force delete branch            | Deleted branch ...      |

---

**Tip:**

- Use descriptive branch names for clarity (e.g., `bugfix/signup-form`).
- If a branch isn’t merged, `-d` is safe; use `-D` **only** if you’re sure you don’t need it!
