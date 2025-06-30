# Removing and Restoring a File in Git (with File History)

This guide explains how to remove a file, view its commit history, and restore it if needed.  
It also covers the use of `--` to disambiguate file paths in git commands.

---

## 1. Remove a File

```bash
git rm toc.txt
```

- Stages the removal (deletion) of `toc.txt` for the next commit.

---

## 2. Commit the Removal

```bash
git commit -m "Remove toc.txt"
```

- Records the deletion of `toc.txt` in the repository history.

---

## 3. Check the File's Commit History

#### Common mistake (no output):

```bash
git log --oneline toc.txt
```

- This does **not** show history after the file is deleted, because `git log` interprets `toc.txt` as a revision if it
  no longer exists.

#### The correct way (shows history for deleted files):

```bash
git log --oneline -- toc.txt
```

- The `--` tells git, "everything after this is a file or path, not a revision."
- Example output:
    ```
    dbd8b36 (HEAD) Remove toc.txt
    ca49180 Initial commit.
    ```
- Shows all commits that affected `toc.txt`, even after it has been deleted.

---

## 4. Restore the Deleted File from an Old Commit

```bash
git checkout ca49180 toc.txt
```

- Restores `toc.txt` as it was in commit `ca49180`.
- Output:
    ```
    Updated 1 path from 9b62c58
    ```
- `toc.txt` is now staged for addition.

---

## 5. Check the Staged Status

```bash
git status -s
```

- Shows short status; you’ll see:
    ```
    A  toc.txt
    ```
- `A` means the file is staged for addition.

---

## 6. Commit the Restoration

```bash
git commit -m "Restore toc.txt"
```

- Commits the restored file back to the repository.

---

## Summary Table

| Command                         | What it does                                             |
|---------------------------------|----------------------------------------------------------|
| git rm toc.txt                  | Stages the removal of toc.txt                            |
| git commit -m "Remove toc.txt"  | Commits the file removal                                 |
| git log --oneline -- toc.txt    | Shows the full history for toc.txt (even if deleted)     |
| git checkout <commit> toc.txt   | Restores the file from a specific commit                 |
| git status -s                   | Shows the status of files (A = added, D = deleted, etc.) |
| git commit -m "Restore toc.txt" | Commits the restored file                                |

---

**Tip:**  
Always use `--` before the filename in `git log` to ensure git treats it as a file path, especially if the file no
longer exists!
