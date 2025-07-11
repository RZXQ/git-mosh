### 1. Start on Feature Branch, Make Changes

``` bash
git switch feature
echo hello >> hello.js
vi hello.js          # Edit if needed
git add hello.js     # Stage the new file
git commit -m "feature: initial hello.js"
```

### 2. Switch to Main and Make Different Change

``` bash
git switch main
vi hello.js
git add hello.js
git commit -m "main: update hello.js"
```

### 3. Try to Merge Feature Into Main

``` bash
git merge feature
```

- **If there are overlapping changes to `hello.js`, you’ll get a conflict (merge fails):**

``` 
Auto-merging hello.js
CONFLICT (content): Merge conflict in hello.js
Automatic merge failed; fix conflicts and then commit the result.
```

## 4. Resolving a Merge Conflict (Three-Way Merge Step)

1. **Open the conflicted file:**
   Look for sections marked by:

``` 
   <<<<<<< HEAD
   # your main branch's changes
   =======
   # feature branch's changes
   >>>>>>> feature
```

1. **Edit** to combine changes as needed.
2. **Mark file as resolved:**

``` bash
   git add hello.js
```

1. **Complete the merge with a commit:**

``` bash
   git commit
```

Now the history includes a merge commit that has two parents—one from `main`, one from `feature`.
This is a classic "three-way merge."

## Visualize with a Graph

``` bash
git log --oneline --all --graph
```

## Summary Table

| Step             | Command                        | Description                                          |
|------------------|--------------------------------|------------------------------------------------------|
| Edit file        | vi hello.js                    | Make change in each branch                           |
| Commit           | git commit -am "message"       | Save your work                                       |
| Switch branches  | git switch main                | feature                                              | Move between branches |
| Merge            | git merge feature              | Attempt to combine; triggers 3-way merge on conflict |
| Resolve conflict | Edit file, git add, git commit | Manually fix, stage, and finish the merge            |

A three-way merge is automatic if changes don’t overlap. If they do, Git asks you to manually combine the edits. **Tip:
**
