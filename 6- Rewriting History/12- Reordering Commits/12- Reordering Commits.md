## Reordering Commits with Interactive Rebase
You can rearrange the order of your recent commits by using interactive rebase and simply moving the lines up or down in the rebase editor.
### 1. Decide How Many Commits to Edit
Count the commits you want to reorder (in your log: `hello`, `world`, `empty`).
### 2. Start Interactive Rebase
Start the rebase from just before your oldest target commit. For the latest three commits, use:
``` bash
git rebase -i HEAD~3
```
### 3. Move Commits in the Editor
The rebase editor will open and show your recent commits like this (most recent at the top):
``` 
pick a43d370 hello
pick ea3d484 world
pick 6199b9a empty
```
To move **"hello"** before **"world"**, just switch their order. For example, to make "world" come before "hello":
``` 
pick ea3d484 world
pick a43d370 hello
pick 6199b9a empty
```
- Move the **lines** representing the commits up or down as needed.

### 4. Save and Finish
Save and close the editor.
Git will automatically reapply the commits in the new order.
- If you have conflicts, Git will pause and ask you to resolve them. After resolving, use:
``` bash
  git rebase --continue
```
Repeat until the rebase is complete.
**That's it!**
Your commits are now reordered as you specified, with "hello" now after "world".
