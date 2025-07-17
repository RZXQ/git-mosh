# Git Workflow: Sharing and Cleaning Up Feature Branches

This guide shows how to share a feature branch with others, push to a remote, and later clean up both remote and local copies.

---

## 1. Create and switch to a new feature branch

```bash
git switch -c feature/change-password
```
Creates and switches to a new branch called for your work. `feature/change-password`

## 2. (Optional) Make and commit your changes
``` bash
# Edit files as needed, then:
git add .
git commit -m "Describe your changes"
```
## 3. Try pushing the new branch to the remote (fails if upstream not set)
``` bash
git push
```
_If the branch has no upstream, you'll see an error. Git suggests the correct command:_
## 4. Push your branch to the remote and set upstream tracking
``` bash
git push -u origin feature/change-password
```
Pushes your branch to the `origin` remote and sets it to track . `origin/feature/change-password`
## 5. Check all local branches and their upstream status
``` bash
git branch -vv
```
Shows local branches with details about which remote (if any) they track.
## 6. List all remote branches
``` bash
git branch -r
```
Shows all branches available on the remote.
## 7. Delete the branch from the remote (after merging or if no longer needed)
``` bash
git push -d origin feature/change-password
```
Removes the branch from the remote repository.
## 8. Confirm branch deletion on the remote
``` bash
git branch -r
```
Ensure the remote branch is gone.
## 9. Delete the local branch (if you don't need it anymore)
``` bash
git branch -d feature/change-password
```
Deletes the branch locally.
_If the branch is not fully merged, use `-D` instead of to force delete.`-d`_
## 10. Check final branch status
``` bash
git branch -vv
```
See which branches remain locally and what remotes they track.
**Summary Table**

| Task                   | Command                       |
|------------------------|-------------------------------|
| Create & switch branch | `git switch -c <branch>`      |
| Push & set upstream    | `git push -u origin <branch>` |
| List local branches    | `git branch -vv`              |
| List remote branches   | `git branch -r`               |
| Delete remote branch   | `git push -d origin <branch>` |
| Delete local branch    | `git branch -d <branch>`      |
