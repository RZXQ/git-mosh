### 1. Add the Original Repo (Upstream) Once

First, make sure you have a remote link to the original repository.
(You only do this **once per project**.)

``` bash
git remote add upstream https://github.com/ORIGINAL_OWNER/REPO.git
# For example:
# git remote add upstream https://github.com/mosh-hamedani/videly-mvc5.git
```

You can check your remotes at any time with:

``` bash
git remote -v
# Should now see both 'origin' (your fork) and 'upstream' (original)
```

### 2. Fetch the Latest Changes from the Original Repo

This pulls the latest changes from the upstream repository into your local repository, but doesn’t merge them yet.

``` bash
git fetch upstream
```

### 3. Update Your Local Main Branch

Switch to your local `main` branch (or `master`, if that's the default), then merge the changes from upstream:

``` bash
git switch main
git merge upstream/main
```

If there is no conflict, your main branch now matches the original repository.

### 4. Push the Updated Main Branch to Your GitHub Fork

So your GitHub fork also gets the updates:

``` bash
git push origin main
```

### 5. (Optional) Update Your Feature or Bugfix Branch

If you’re working on another branch (like `bugfix` or `feature`), update it with the latest `main`:

``` bash
git switch your-feature-branch
git merge main
# Or, if you want a cleaner history, use rebase:
# git rebase main
```

This helps avoid conflicts later.

### Quick Summary Table

| Step                        | Command(s)                                      | Description                |
|-----------------------------|-------------------------------------------------|----------------------------|
| 1. Add upstream repo (once) | `git remote add upstream <repo-url>`            | Link to the original repo  |
| 2. Fetch upstream changes   | `git fetch upstream`                            | Download new commits       |
| 3. Merge upstream into main | `git switch main`                               
 `git merge upstream/main`   | Update your local main                          |
| 4. Push to your fork        | `git push origin main`                          | Update your fork on GitHub |
| 5. Update feature branch    | `git switch my-feature`                         
 `git merge main`            | Get the latest changes into your working branch |

**Notes:**

- If you make mistakes with remote names, you can rename or remove them using `git remote rename` or `git remote rm`.
- If you get merge conflicts, you’ll need to resolve them, then and `git commit` as needed. `git add .`
- Always make sure to keep your local and forked main branches up to date with the original, especially before starting
  new work.
