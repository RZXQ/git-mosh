### Revised Tutorial: Splitting a Commit into Two Commits

Suppose your commit history is:

``` 
* 93a18cd (HEAD -> main) combined words
* 3ac8396 clean up all the words
```

You realize that `combined words` contains changes that should be in two different commits. Here’s how to split it:

#### 1. Start Interactive Rebase

Begin an interactive rebase at the commit you want to split:

``` bash
git rebase -i 93a18cd^
```

Change the line for the commit to `edit` in the rebase editor:

``` 
edit 93a18cd combined words
```

#### 2. Unstage All Changes

Pause at this commit and unstage all the changes:

``` bash
git reset --mixed HEAD^
```

Now all changes from that commit are in your working directory as unstaged files.

#### 3. Add & Commit in Parts

Carefully add only the changes that should be in the first new commit:

``` bash
git add <file1> <file2> ...
git commit -m "Describe the first part"
```

Add and commit the remaining changes:

``` bash
git add <other files>
git commit -m "Describe the second part"
```

#### 4. Finish the Rebase

Continue the rebase process:

``` bash
git rebase --continue
```

If there are no conflicts or more steps, you’re done!
