# Git: Understanding `reset` and `revert` (With Live Examples)

Suppose your repo has two branches: `main` and `bug`.

### Example log for `main`:

``` 
e54864e (HEAD -> main) Fix typo
819aaa3 Initial commit
```

## 1. `git reset` — Change History by Moving the Branch Pointer

**Warning:**
will **DELETE commits from your branch** (if used on the latest branch pointer). `git reset --hard`

#### Example: Move `main` back by one commit

``` bash
git reset --hard HEAD~1
```

**Output:**

``` 
HEAD is now at 819aaa3 Initial commit
```

**History now:**

``` bash
git log --oneline
```

``` 

819aaa3 (HEAD -> main) Initial commit
```

The last commit (`e54864e`) is gone from your `main` branch!

#### Example: Move branch pointer forward again (`e54864e` is still in your local repo)

``` bash
git reset --hard e54864e
```

**Output:**

``` 
HEAD is now at e54864e Fix typo
```

**History now:**

``` bash
git log --oneline
```

``` 

e54864e (HEAD -> main) Fix typo
819aaa3 Initial commit
```

> **Important:**
> If you use `reset` on a branch you share with others (pushed to GitHub), it causes history errors for them!
> Only your **own** branches, never shared history. `reset --hard`
>

## 2. `git revert` — Undo a Commit With a New Commit

**Safer for teamwork!**

- `git revert <commit>` makes a new commit that undoes the named commit.
- It does NOT delete history.

#### Revert the most recent commit:

Assume this is your history:

``` 
e54864e (HEAD -> main) Fix typo
819aaa3 Initial commit
```

``` bash
git revert HEAD
```

**Output:**

``` 
[main xxxxxxx] Revert "Fix typo"
 1 file changed, 1 insertion(+), 1 deletion(-)
```

**History now:**

``` bash
git log --oneline
```

``` 

xxxxxxx (HEAD -> main) Revert "Fix typo"
e54864e Fix typo
819aaa3 Initial commit
```

**Result:**
The "fix typo" changes are undone, but all commits remain!

## 3. — Reverting a Merge Commit `git revert -m 1 HEAD`

Merge commits are special. They have **two parents**:

- The branch you were on (`main`), and
- The branch you merged in (`bug`).

Git needs to know which you want as your "mainline" when undoing a merge.

### What does mean? `-m 1`

- is **mainline**. `-m`
- means to keep **parent 1** as the mainline (usually the branch you were on when merging). `-m 1`

### Example: Reverting a Merge

Suppose your log looks like:

``` 
*   abcd123 (HEAD -> main) Merge branch 'bug'
|\
| * 4567890 (bug) Fix a bug!
|/
* 1234567 Initial commit
```

`abcd123` is a **merge commit**.

#### Trying a plain revert:

``` bash
git revert HEAD
```

**Output:**

``` 
error: Commit abcd123 is a merge but no -m option was given.
fatal: revert failed
```

**You must specify which branch to treat as the "mainline"!**

#### Correct way (to undo the merge on `main`):

``` bash
git revert -m 1 HEAD
```

**Output:**

``` 
[main bbbbbbb] Revert "Merge branch 'bug'"
 1 file changed, 1 deletion(-)
```

**History now:**

``` 
* bbbbbbb (HEAD -> main) Revert "Merge branch 'bug'"
*   abcd123 Merge branch 'bug'
|\
| * 4567890 (bug) Fix a bug!
|/
* 1234567 Initial commit
```

- The merge is undone, but all commits remain.
- This creates a special revert commit to "negate" the changes from the merge.

## 4. Summary Table

| Command                          | What it does                               | Output example       | Safe for teamwork? |
|----------------------------------|--------------------------------------------|----------------------|--------------------|
| `git reset --hard HEAD~1`        | Moves branch pointer back, deletes commits | HEAD is now at ...   | NO                 |
| `git reset --hard <commit>`      | Moves to any commit, deletes newer         | HEAD is now at ...   | NO                 |
| `git revert HEAD`                | Undoes latest commit with new commit       | [main xxx] Revert... | YES                |
| `git revert -m 1 <merge-commit>` | Undoes a merge commit, keep parent 1       | [main xxx] Revert... | YES                |

## 5. Visual Comparison

### After (deletes commits): `git reset --hard`

``` 
Before:    A -- B -- C (HEAD -> main)
After:     A -- B (HEAD -> main)
```

### After `git revert` (adds "undo" commits):

``` 
A -- B -- C -- D (HEAD -> main)
             ^     ^
            undo   original change
```

History is preserved—great for working on teams!

## 6. Tips and Best Practices

- **Avoid on public/shared branches.`git reset --hard`**
- **Use `git revert` to undo, especially for merges!**
- Use when reverting a merge commit, to tell git which side to keep as the "mainline". `-m 1`

## 7. Quick Checklist

| Use If…                                                   | Command                               |
|-----------------------------------------------------------|---------------------------------------|
| You just want to undo your last local commit (not pushed) | `git reset --hard HEAD~1`             |
| You want to _undo_ a commit without deleting history      | `git revert <commit>`                 |
| You want to _undo a MERGE_                                | `git revert -m 1 <merge-commit-hash>` |

If you ever need to know which parent is "1" or "2" on your merge, run:

``` bash
git show <merge-commit-hash>
```

Look for the lines:

``` 
Merge: 1234567 4567890
```

- The **first hash** (`1234567`) is parent 1 (mainline).
- The **second** is parent 2.