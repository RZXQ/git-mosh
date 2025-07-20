## Dropping Commits with Interactive Rebase

Sometimes you want to remove specific commits from your branch history. Here’s how you can do this with an interactive
rebase:

### 1. Decide Which Commits to Drop

First, figure out which commits you want to remove.
You'll start the rebase _just before_ the oldest commit you want to drop.

### 2. Start the Interactive Rebase

Start an interactive rebase using the parent of the oldest commit you want to modify. For example, if you want to edit
the last 3 commits:

``` bash
git rebase -i HEAD~3
```

Replace `3` with the number of recent commits you want to review and possibly drop.

### 3. Edit the Rebase List

A text editor will open with a list of recent commits. Each line starts with `pick`:

``` 
pick <hash> Commit message
pick <hash> Commit message
pick <hash> Commit message
```

To **drop** a commit, change `pick` at the beginning of its line to `drop`.
For example, to remove two commits:

``` 
drop <hash1> Commit you want to remove
drop <hash2> Another commit to remove
pick <hash3> Commit to keep
```

Keep `pick` on lines you want to keep.

### 4. Save and Continue

Save and close the editor to apply the changes.
If Git asks for resolutions, fix them, then run:

``` bash
git rebase --continue
```

Repeat this step as needed until the rebase is complete.
**Result:**
The commits you marked as `drop` are now removed from your branch history.
