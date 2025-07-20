### Tutorial: Changing a Commit Message with Interactive Rebase

If you want to change the message of a previous commit, interactive rebase makes it easy:

1. **Start the interactive rebase**
   Choose the commit just before the one you want to reword:

``` bash
   git rebase -i <commit-hash>^
```

Replace `<commit-hash>` with the hash of the commit you want to change.

1. **Edit the command list**
   In the editor, find the line for the commit to edit.
   Change `pick` to `reword` for that commit:

``` 
   reword 6109551 hell
   pick   b875012 word
```

1. **Save and provide the new message**
   Save and close the editor.
   Git will prompt you for the new commit message—edit it, save, and close the editor again.
2. **Finish the rebase (if prompted)**
   If there are no conflicts, the rebase will complete. Otherwise, follow any prompts to resolve them.
