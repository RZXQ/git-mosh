## Squashing Commits with Interactive Rebase

Suppose you have this commit log (most recent at the top):

``` 
* 2e0e6ad (HEAD -> main) Finish
* 32715b2 Hello
* 182798c World
* 6199b9a empty
```

If you want to squash the “World” and “Hello” commits into “Finish”, here are the steps:

### 1. Start Interactive Rebase

Start the interactive rebase from the commit **just before** the oldest commit you want to squash:

``` bash
git rebase -i 182798c^
```

### 2. Mark Commits to Squash

In the text editor that opens, you’ll see lines for each commit in this order:

``` 
pick 182798c World
pick 32715b2 Hello
pick 2e0e6ad Finish
```

To squash the two earlier commits into "Finish", modify like this:

``` 
squash 182798c World
squash 32715b2 Hello
pick 2e0e6ad Finish
```

Alternatively, using `fixup`:

``` 
fixup 182798c World
fixup 32715b2 Hello
pick 2e0e6ad Finish
```

- `squash` will prompt you to update the commit message.
- `fixup` skips the message and just merges the changes.

> **Tip:**
> The order and instructions (`pick`, `squash`, or `fixup`) determine **which commit message remains** and how changes
> are combined.
>

### 3. Finish the Rebase

- Save and close the editor.
- Git will now combine those commits.
- If you used `squash`, you can edit the final commit message.
- If you get conflicts, resolve them and then run:

``` bash
  git rebase --continue
```

- Repeat until the rebase completes.

## Summary Table

| Command                                                       | Purpose                                  |
|---------------------------------------------------------------|------------------------------------------|
| `git rebase -i <commit>^`                                     | Start interactive rebase                 |
| Change `pick` to `squash` or `fixup` for the commits to merge | Mark commits to squash into previous one |
| Save and close editor                                         | Start rebasing                           |
| (as needed) `git rebase --continue`                           | Continue after conflicts                 |
