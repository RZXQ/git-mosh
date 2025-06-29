# Git Restore and Clean: Step-by-Step with Examples

## 1. Check the Current Status

```bash
git status -s
```

- This shows a short summary of your repository.
- Example output:
    ```
     M file1.txt      # file1.txt is modified in the working directory, not staged
    ?? file2.txt      # file2.txt is untracked (new, not added to git)
    ```

---

## 2. Restore File Changes

```bash
git restore file1.txt
```

- This command copies the **staged version** (if any) or the last committed version of `file1.txt` into your working
  directory.
- Effect: Any unsaved changes in `file1.txt` in your working directory are **undone** (reverted to what is staged or
  last committed).
- **Warning:** Local changes you made to this file will be lost.

---

```bash
git restore .
```

- This command undoes **all local changes** in the working directory for all tracked files.
- Effect: Every modified file goes back to its last committed (or staged) state.
- **Warning:** All your unsaved changes in any tracked file will be lost.

---

## 3. Untracked Files Example

```bash
echo sdf >> file3.txt
git status -s
```

- This creates a new file called `file3.txt`.
- `git status -s` now shows:
    ```
    ?? file3.txt       # file3.txt is untracked (not added to git)
    ```

---

## 4. Cleaning Untracked Files

If you try to clean untracked files:

```bash
git clean
```

- You might see this error:
    ```
    fatal: clean.requireForce defaults to true and neither -i, -n, nor -f given; refusing to clean
    ```
- This means git wants you to confirm before deleting files.

---

### Clean Untracked Files and Directories

```bash
git clean -fd
```

- `f` means **force**: Actually delete the files/directories (required for safety).
- `d` means **directories**: Also remove untracked directories, not just files.
- Effect: All untracked files (like `file3.txt`) and untracked directories are deleted from your working directory.
- **Warning:** This cannot be undone! Use with care.

---

## Summary Table

| Command               | What it does                                               |
|-----------------------|------------------------------------------------------------|
| git status -s         | Shows short status (staged, modified, untracked files)     |
| git restore file1.txt | Reverts file1.txt to last staged/committed version         |
| git restore .         | Reverts all tracked files to last staged/committed version |
| git clean -fd         | Deletes all untracked files and directories (force + dirs) |

---