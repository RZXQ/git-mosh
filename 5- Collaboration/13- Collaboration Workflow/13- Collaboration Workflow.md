# Example Git Branch Collaboration Workflow

## 1. Create the Feature Branch on GitHub

Create a new branch on GitHub: `feature/change-password`

---

## 2. Fetch and Track the New Branch Locally

```bash
git fetch git branch -r
# Shows: origin/feature/change-password

git switch -c feature/change-password origin/feature/change-password
# Now tracking the remote branch locally
``` 

---

## 3. Simulate a Collaborator (Amy) Working

```bash
# In a new terminal/workspace:
mkdir amy cd amy git clone [https://github.com/RZXQ/repo.git](https://github.com/RZXQ/repo.git)
# Amy only has 'main' checked out locally.

git branch -r
# Shows: origin/feature/change-password

git switch -c feature/change-password origin/feature/change-password
# Now Amy is on the feature branch and tracking the remote.
``` 

---

## 4. Amy Makes and Pushes Changes

```bash
bash echo password >> file1.txt

git add .

git commit -am "Amy gonna push" git push
``` 

---

## 5. You Pull Amy's Changes

```bash
git switch feature/change-password git pull
# Review the latest changes
``` 

---

## 6. Merge the Feature Branch into Main

```bash
git switch main 

git merge feature/change-password 

git push
``` 

---

## 7. Delete the Feature Branch (Both Remote and Local)

```bash
git push -d origin feature/change-password 

git branch -d feature/change-password
``` 

---

## 8. Collaborator Cleans Up

``` bash
# On Amy's machine:
git switch main 

git pull # Get any changes from your merge 

git branch -d feature/change-password # Delete local branch 

git remote prune origin # Clean up removed remote-tracking branches
``` 

---

## Summary

- **New feature branch is created on GitHub.**
- **Both you and your collaborator set up local tracking branches.**
- **Commits are made and pushed.**
- **Work is merged back to main, branch is deleted.**
- **Collaborators delete their own local branches and prune remote-tracking references.**