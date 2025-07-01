# Using `git stash` to Save and Restore Local Changes (with Command Outputs)

This guide shows how to use `git stash` to temporarily store and manage uncommitted changes, with real command outputs
for each step.

---

## 1. Problem: Switching Branches with Uncommitted Changes

If you edit a file and try to switch branches:

```bash
vi audience.txt   # (add some text)
git switch bugfix/signup-form
```

**Output:**

```
error: Your local changes to the following files would be overwritten by checkout:
	audience.txt
Please commit your changes or stash them before you switch branches.
```

- **Solution:** Stash your changes.

---

## 2. Stash Only Tracked Changes

```bash
git stash push -m "New tas rules."
```

- Stashes only changes to tracked files.
- **Note:** New untracked files (e.g., newfile.txt) are NOT stashed by default.

---

## 3. Stash Including Untracked Files

```bash
echo hello >> newfile.txt   # create an untracked file
git stash push -a -m "My new stash."
```

- `-a` or `--include-untracked` stashes both tracked and untracked files.

---

## 4. List All Stashes

```bash
git stash list
```

**Output:**

```
stash@{0}: On bugfix/signup-form: stash all
stash@{1}: On main: My new stash.
```

- Each stash is numbered, newest is `stash@{0}`.

---

## 5. Show What a Stash Contains

```bash
git stash show stash@{1}
# or
git stash show 1
```

**Output:**

```
 audience.txt | 5 +++--
 1 file changed, 3 insertions(+), 2 deletions(-)
```

- Shows which files and how many lines changed.

---

## 6. Apply a Stash

```bash
git stash apply 0
```

**Output:**

```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   audience.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.idea/

no changes added to commit (use "git add" and/or "git commit -a")
```

- Applies the changes from the stash to your working directory.
- **Note:** The stash is NOT removed after applying.

---

## 7. Drop a Specific Stash

```bash
git stash drop 0
```

- Deletes `stash@{0}` from the stash list.

---

## 8. Clear All Stashes

```bash
git stash clear
```

- Removes all stashes.

---

## Summary Table

| Command                    | Description                          | Example Output / Notes         |
|----------------------------|--------------------------------------|--------------------------------|
| git stash push -m "msg"    | Stash tracked changes with a message |                                |
| git stash push -a -m "msg" | Stash tracked & untracked changes    |                                |
| git stash list             | List all stashes                     | stash@{0}: On ...              |
| git stash show <stash>@{N} | Show summary of changes in a stash   | file                           | lines changed                 |
| git stash apply N          | Apply stash N to working directory   | changes applied, stash remains |
| git stash drop N           | Delete stash N                       |                                |
| git stash clear            | Delete all stashes                   |                                |

---

**Tip:**

- Use `git stash` to quickly save and restore work-in-progress changes without committing!
- Remember, after `git stash apply`, the stash still exists until you drop it.