# Fetching in Git: `git fetch` Explained

The `git fetch` command retrieves the latest commits, branches, and tags from a remote repository, updating your local
copy of those references—but it does **not** modify your working directory or current branches. It’s a safe way to see
what’s new on the remote before making any changes to your files.

---

## Basic Fetch Workflow

```
bash git fetch
``` 

- This downloads any new changes from your remote (usually called `origin`) for all branches, but does **not** merge
  them into your current branch.

---

## Checking Branch Status After Fetching

You can then check the status of your local branches relative to their remote counterparts:

```
bash git branch -vv
``` 

**Sample Output:**

```
- main 9db7724 [origin/main: ahead 3] Merge remote-tracking branch 'origin/main'
``` 

- The output shows:
    - Your current branch (`main`)
    - The latest commit (`9db7724`)
    - The status compared to the remote (`ahead 3` means you have 3 commits locally that aren’t on `origin/main` yet)

---

## Merging Changes from the Remote

After fetching, **to bring remote changes into your current branch**, use `git merge` with the remote tracking branch:

```
bash git merge origin/main
``` 

- This merges changes from `origin/main` into your current branch.
- No merge occurs automatically with `git fetch`—you decide when to integrate the updates.

---

## Quick Reference Table

| Command               | What it Does                                                 |
|-----------------------|--------------------------------------------------------------|
| git fetch             | Downloads new data from the remote repo                      |
| git branch -vv        | Shows branch tracking info and how many commits ahead/behind |
| git merge origin/main | Merges fetched (but not-yet-merged) changes from remote      |

---

**Tips:**

- Use `git fetch` regularly to keep your local repository up-to-date with the remote.
- Use `git pull` if you want to fetch and merge in a single step (but `git fetch` gives you more control to review
  changes first).