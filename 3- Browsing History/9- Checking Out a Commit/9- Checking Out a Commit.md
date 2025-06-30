# Understanding Detached HEAD State with `git checkout`

## 1. Checking Out a Specific Commit

```bash
git checkout dad47ed
```

- Switches your working directory to the commit with hash `dad47ed`.
- **You are now in a "detached HEAD" state**:
    - `HEAD` points directly to the commit `dad47ed`, not to any branch.
    - You can browse the project as it was at this commit, make experimental changes or commits.
    - Any new commits here are NOT on a branch. If you switch away, you could lose them unless you create a new branch.

**Output message explained:**

- You can make experimental changes and commit, but these commits are not attached to a branch.
- To keep any new commits, create a new branch:
    ```bash
    git switch -c <new-branch-name>
    ```
- To return to your previous branch:
    ```bash
    git switch -
    ```

---

## 2. Branches and HEAD

- `master` (or `main`) points to the latest commit on that branch.
- `HEAD` points to:
    - The latest commit of the currently checked out branch (usually).
    - Or, in detached HEAD state, directly to a specific commit (like `dad47ed`).

---

## 3. Viewing All Commits in the Repo

```bash
git log --oneline --all
```

- Shows a compact list of all commits from every branch in your repository.
- Useful for seeing where branches and commits are in history.

---

## 4. Switch Back to the Master Branch

```bash
git checkout master
```

- Switches your working directory back to the `master` branch.
- `HEAD` now points to the tip (latest commit) of `master`.
- Any new commits you make will be added to `master`.

---

## Summary Table

| Command                 | What it does                                                         |
|-------------------------|----------------------------------------------------------------------|
| git checkout <commit>   | Switches to a specific commit (detached HEAD), not a branch          |
| git log --oneline --all | Shows all commits in a compact format                                |
| git checkout master     | Returns to the master branch, HEAD points to the latest commit there |

---

**Tip:**  
If you want to keep work done in a detached HEAD, create a branch with `git switch -c mybranch` before switching away!
