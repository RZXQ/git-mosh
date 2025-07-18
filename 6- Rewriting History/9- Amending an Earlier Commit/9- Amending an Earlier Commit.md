# Tutorial: Amending Commits During Interactive Rebase

This guide demonstrates how to use `git rebase -i` (interactive rebase) to amend past commits, such as adding forgotten
files or updating commit messages. This is useful for cleaning up your commit history before sharing your changes.

---

## 1. View Commit History

Start by viewing a condensed graph of your commit history:

``` bash 
git log --oneline --all --graph
``` 

Sample output:

```
a6d03aa (HEAD -> master) Render cafes on the map. 3d8e437 Revert bad code. f666091 WIP 111bd75 Update terms of service and Google Map SDK version. 72856ea WIP 8441b05 Add a reference to Google Map SDK. 8527033 Change the color of restaurant icons. af26a96 Fix a typo. 6fb2ba7 Render restaurants the map. 70ef834 Initial commit.
``` 

---

## 2. Start Interactive Rebase

To edit or amend an old commit, start an interactive rebase back to just before the earliest commit you’d like to
change.  
For example, to edit commits after `8527033`:

``` bash 
git rebase -i 8527033
``` 

You’ll see a list like this in your editor:

```
pick 8441b05 Add a reference to Google Map SDK. 
pick 72856ea WIP 
pick 111bd75 Update terms of service and Google Map SDK version. 
pick f666091 WIP 
pick 3d8e437 Revert bad code. 
pick a6d03aa Render cafes on the map.
``` 

Change `pick` to `edit` on the commit you want to amend:

```
edit 8441b05 Add a reference to Google Map SDK. 
pick 72856ea WIP 
pick 111bd75 Update terms of service and Google Map SDK version. 
pick f666091 WIP 
pick 3d8e437 Revert bad code. 
pick a6d03aa Render cafes on the map.
``` 

Save and close the editor.

---

## 3. Amend the Commit

Git will stop at the commit marked `edit`.  
Now, you can add or change files as needed. For example, suppose you want to add a missing `license.txt`:

``` bash 
echo license > license.txt 

git add license.txt 

git commit --amend
``` 

- Edit the commit message if necessary during the amend process.
- Your changes are now included in the chosen commit.

---

## 4. Inspect the History

At this point, your amended commit will get a new commit hash. You can view the updated graph with:

``` bash 
git log --oneline --all --graph
``` 

You'll see both the old and the new commit graphs while the rebase is in progress.

---

## 5. Continue or Abort the Rebase

To move on to the next step in your rebase:

``` bash 
git rebase --continue
``` 

Repeat this process for any further commits you want to amend (Git will pause at each `edit`).  
If you need to stop and undo everything, use:

``` bash 
git rebase --abort
``` 

---

## 6. Final Commit History

Once the rebase completes, your commit history will reflect the amended changes, with new commit hashes for those you
changed.

---

### Quick Reference Table

| Task                                  | Command(s)                                   |
|---------------------------------------|----------------------------------------------|
| Start interactive rebase              | `git rebase -i <base_commit>`                |
| Mark commit for editing               | Change `pick` to `edit` in the rebase script |
| Add or modify files in stopped commit | Usual `git add`, `git rm`, or edit as needed |
| Amend the commit                      | `git commit --amend`                         |
| Finish the rebase                     | `git rebase --continue`                      |
| Abort all changes from the rebase     | `git rebase --abort`                         |

---

**Tip:**  
Interactive rebasing lets you clean up history by rewriting commits, combining them, or fixing mistakes—even after
they've happened!

Let me know if you want more details on advanced rebase actions, split/squash workflows, or interactive rebase tricks!

```
