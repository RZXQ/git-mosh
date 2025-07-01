# Merging Branches in Git: Fast-Forward, No Fast-Forward, and Visual Logs

This guide shows you the difference between fast-forward and no fast-forward merges, and how to visualize your branch
history with `git log --oneline --all --graph`. Real command outputs are provided for each step.

---

## 1. View the Commit Graph

```bash
git log --oneline --all --graph
```

**Output Example:**

```
* 05d3fdc (HEAD -> main, bugfix/signup-form) Fix the bug that prevented the users from signing up.
* a642e12 Add header to all pages.
* 50db987 Include the first section in TOC.
...
```

- Shows all commits as a graph, with branch pointers.

---

## 2. Fast-Forward Merge

Suppose you're on `main` and merge a branch that is ahead by a linear history:

```bash
git merge bugfix/signup-form
```

**Output:**

```
Updating a642e12..05d3fdc
Fast-forward
 audience.txt | 5 ++---
 1 file changed, 2 insertions(+), 3 deletions(-)
```

- Main moves directly to the branch tip without a merge commit.

**Graph after fast-forward:**

```
* 05d3fdc (HEAD -> main, bugfix/signup-form) Fix the bug that prevented the users from signing up.
* a642e12 Add header to all pages.
...
```

---

## 3. Create and Work on a New Branch

```bash
git branch bugfix
git switch bugfix
# (decide to use a better name)
git switch -C bugfix/login-form  # rename and switch
vi toc.txt  # make changes
git add .
git commit -m "Update toc.txt"
```

- Now you have a new branch and a commit.

---

## 4. Graph After Creating a New Feature Branch

```bash
git log --oneline --all --graph
```

**Output:**

```
* ac67eab (HEAD -> bugfix/login-form) Update toc.txt
* 05d3fdc (main, bugfix/signup-form) Fix the bug that prevented the users from signing up.
* a642e12 Add header to all pages.
...
```

- `bugfix/login-form` is ahead of main.

---

## 5. Merge With No Fast-Forward (`--no-ff`)

Switch to `main` and merge:

```bash
git switch main
git merge --no-ff bugfix/login-form
```

- `--no-ff` always creates a merge commit, preserving the branch structure.

**Graph after no-ff merge:**

```
*   344f06a (main) Merge branch 'bugfix/login-form'
|\  
| * ac67eab (HEAD -> bugfix/login-form) Update toc.txt
|/  
* 05d3fdc (bugfix/signup-form) Fix the bug that prevented the users from signing up.
* a642e12 Add header to all pages.
...
```

- The merge commit `344f06a` shows both parent histories, even if a fast-forward would have been possible.

---

## 6. Set `merge.ff` Configuration

### For the Current Repo Only

```bash
git config ff no
```

- Default merges will use `--no-ff` in this repo.

### For All Repos (Global)

```bash
git config --global ff no
```

- All merges you perform will use `--no-ff` by default.

---

## Summary Table

| Command                         | What it does                            | Example Output/Result         |
|---------------------------------|-----------------------------------------|-------------------------------|
| git merge <branch>              | Merges branch, fast-forward if possible | Fast-forward, no merge commit |
| git merge --no-ff <branch>      | Always creates a merge commit           | Merge commit in history       |
| git log --oneline --all --graph | Visualize commit history and branches   | ASCII graph/log               |
| git config ff no                | Set no-ff as default for this repo      |                               |
| git config --global ff no       | Set no-ff as default for all repos      |                               |

---

**Tip:**

- Use `--no-ff` merges to keep a clear history of feature branches, even if Git could fast-forward.
- `git log --oneline --all --graph` is great for visualizing merges and branch structure!
