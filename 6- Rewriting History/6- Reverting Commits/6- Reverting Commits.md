# Git: Reverting Commits & Common Workflows

## 1. Reverting Multiple Commits at Once

Suppose you have this commit history:

``` 
E -- D -- C -- B -- A (HEAD)
```

If you want to revert the last 3 commits (`C`, `D`, `E`):

``` bash
git revert HEAD~3..HEAD
```

- This will create individual "revert" commits for each, starting from (oldest) up to `HEAD` (newest). `HEAD~3`
- If all go smoothly, you'll get three new commits, each undoing one of the selected commits.

## 2. Reviewing & Batching Reverts

If you want to preview all the changes first (and possibly combine the reverts into one commit):

``` bash
git revert --no-commit HEAD~3..HEAD
```

- This stages all the reversions, but does **not** create the commits yet.
- You can review what was changed (use `git status` and `git diff`).
- When ready, commit all the staged changes at once:

``` bash
  git commit -m "Revert last 3 commits as a batch"
```

## 3. Handling Merge Conflicts During Revert

When reverting, especially several commits, you might hit conflicts. If so:

- Git will pause and ask you to fix the files.
- After fixing, stage the resolved files:

``` bash
  git add <filename>
```

- Continue the revert process:

``` bash
  git revert --continue
```

If you realize you made a mistake or need to abort the whole operation:

``` bash
git revert --abort
```

- This will stop the revert and reset your files back to the previous state.

## 4. Important Notes

- Every revert **adds new commits**—it does not erase old commits.
- For shared/pushed branches, **always use revert, not reset**.
- To undo a merge commit, use:

``` bash
  git revert -m 1 <merge-commit-hash>
```

## 5. Quick Workflow Example

**Revert multiple commits (individually):**

``` bash
git revert HEAD~2..HEAD
```

**Batch revert (as a single commit):**

``` bash
git revert --no-commit HEAD~2..HEAD
git commit -m "Batch revert last 3 commits"
```

**Deal with a conflict during revert:**

- Fix any conflicted files.
- `git add <filename>` (mark resolved).
- `git revert --continue`

**Abort an in-progress revert:**

``` bash
git revert --abort
```

## Summary Table

| Command                             | Use Case                                   |
|-------------------------------------|--------------------------------------------|
| git revert                          | Revert a single commit                     |
| git revert HEAD~3..HEAD             | Revert multiple commits individually       |
| git revert --no-commit HEAD~3..HEAD | Revert multiple, but review & batch commit |
| git revert --abort                  | Abort a revert in progress                 |
| git revert --continue               | Continue revert after resolving conflicts  |
| git revert -m 1 <merge-commit-hash> | Revert a merge commit                      |
