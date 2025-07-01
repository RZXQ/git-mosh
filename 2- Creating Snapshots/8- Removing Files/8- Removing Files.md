# Removing Files from Working Directory and Git — Step-by-Step

This guide explains how to remove files from your project, both from the working directory and from Git's tracking, with
step-by-step commands and explanations.

---

## 1. Remove a File from the Working Directory Only

```bash
rm file2.txt
```

- Deletes `file2.txt` from your local folder.
- **Note:** The file is still tracked by Git and not yet staged for deletion.

---

## 2. List All Files Tracked by Git

```bash
git ls-files
```

- Shows all files currently tracked by Git.
- `file2.txt` still appears in this list until you tell Git to remove it.

---

## 3. Stage the Deletion of the File

```bash
git add file2.txt
```

- Stages the removal of `file2.txt` from the repository (tells Git to remove it).
- Now, the next commit will record the file's removal.

---

## 4. Commit the Deletion

```bash
git commit -m "remove unused code"
```

- Records the deletion in your project history.

---

## Alternative: Remove from Both Working Directory and Git in One Step

```bash
git rm file2.txt file1.txt
```

- Deletes the files from the working directory **and** stages their removal at once.
- No need to use `rm` and `git add` separately for these files.

---

## Summary Table

| Command             | What it does                                                |
|---------------------|-------------------------------------------------------------|
| rm file.txt         | Removes local file only; not yet staged for deletion in Git |
| git ls-files        | Lists files tracked by Git (will still show until staged)   |
| git add file.txt    | Stages the deletion of the file in Git                      |
| git commit -m "msg" | Commits the staged deletion                                 |
| git rm file.txt     | Removes file and stages for deletion in one step            |

---

**Tip:**

- Use `rm` + `git add` if you want to control when the file is deleted from Git.
- Use `git rm` for a quicker, combined approach.