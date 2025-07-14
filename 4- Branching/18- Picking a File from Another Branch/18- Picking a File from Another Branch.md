# Copying a File from Another Branch and Committing It

You can update a file on your current branch by bringing in its version from a different branch, without merging all the
other branch’s changes. Here’s how to do it:

---

## 1. Ensure you are on the target branch

Switch to the branch where you want the file updated (for example, `main`):

```bash 

git switch main

``` 

---

## 2. Restore the File from the Source Branch

Replace the file in your working directory with the version from another branch:

```
bash git restore --source=feature/send-email -- toc.txt
``` 

This updates `toc.txt` on your current branch to match the version in `feature/send-email`.

---

## 3. Commit the Change

Record this change:

``` bash

bash git commit -am "Update toc.txt with version from feature/send-email"

``` 

The `-a` flag stages the change if `toc.txt` is tracked, and saves your commit message.

---

## Summary Table

| Step                           | Command                                              | Description                            |
|--------------------------------|------------------------------------------------------|----------------------------------------|
| Switch to target branch        | `git switch main`                                    | Get ready to update the file           |
| Restore file from other branch | `git restore --source=feature/send-email -- toc.txt` | Pull a single file from another branch |
| Commit the update              | `git commit -am "Update toc.txt with version..."`    | Save your update in project history    |

---

**Tip:**  
This workflow is useful when you want the latest update for just a specific file, rather than merging everything from
another branch.

