# Amending, Adding, and Removing Files From Recent Commits in Git

This guide covers practical workflows for correcting recent commits — whether you forgot to add a file, need to tweak
the commit message, or want to undo accidentally added files.

---

## 1. Amending the Last Commit

If you want to add more changes to your most recent commit, or update its message:

``` bash 
echo cafes >> map.txt # Make a change git commit -am "Render cafes on the map" # Initial commit
# Edit the file again
vi map.txt # e.g. change "cafes" to "blue cafes"
git add . # Stage your new changes
# Amend the last commit (keeps the previous message)
git commit --amend
# Or update the commit message at the same time
git commit --amend -m "Render blue cafes on the map"
``` 

**Result:**  
The updated files and/or message are now part of your last commit. Useful for quick fixes before pushing.

---

## 2. If You Forgot to Add a File

If you missed a file in your last commit, add it and amend:

``` bash 
echo hello >> file1.txt # Create the forgotten file
git add . # Stage the new file
git commit --amend # Add it to the previous commit
``` 

**Result:**  
The missed file is now included in the last commit.

---

## 3. If You Accidentally Added an Unwanted File

If your last commit accidentally includes a file you didn’t mean to add, you can “undo” the commit, remove the unwanted
file, and recommit:

``` bash
# Undo the last commit but keep changes unstaged
git reset --mixed HEAD~1
# If you no longer want the file, remove it from the working directory
git clean -fd # Removes all untracked files and directories
git add . # Stage only the files you want
git commit -m "Remove unwanted file from last commit"
``` 

**Result:**  
The last commit is redone without the accidentally added files.

---

## Quick Notes

- Use `git commit --amend` only for commits that haven’t been pushed/shared with others, to avoid confusion.
- `git reset --mixed` undoes the last commit but keeps changes in your working directory for easy adjustment.
- `git clean -fd` is destructive: it deletes untracked files permanently. Double-check files before running.

---

**Summary Table**

| Task                                       | Command(s)                                                                         |
|--------------------------------------------|------------------------------------------------------------------------------------|
| Add changes / fix message in last commit   | `git add .` + `git commit --amend` or `git commit --amend -m "New message"`        |
| Add a missed file to last commit           | `git add file` + `git commit --amend`                                              |
| Remove file accidentally added to a commit | `git reset --mixed HEAD~1` + `git clean -fd` + `git add .` + `git commit -m "..."` |

---
