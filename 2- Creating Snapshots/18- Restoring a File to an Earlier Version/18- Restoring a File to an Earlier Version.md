# Removing and Restoring Files in Git

## 1. Remove a File from Both Working Directory and Staging Area

```bash
git rm file1.txt
```

- This command **deletes** `file1.txt` from your working directory (your local files) **and** stages this deletion for
  the next commit.
- The file will be gone from your folder and will be marked as staged for deletion.

---

## 2. Check the Status After Removal

```bash
git status -s
```

- Example output after `git rm`:
    ```
    D  file1.txt
    ```
- `D` means the file is staged to be deleted in the next commit.

---

## 3. Commit the Deletion

```bash
git commit -m "Delete file1.txt"
```

- This permanently records the deletion of `file1.txt` in your repository.
- The file is now gone from your project in the latest commit.

---

## 4. Restore a Deleted File from a Previous Commit

```bash
git restore --source=HEAD~1 file1.txt
```

- This command restores the version of `file1.txt` from the previous commit (`HEAD~1`) into your working directory.
- Effect: If you deleted `file1.txt` and committed that deletion, this command brings it back as it was one commit ago.
- The file will reappear in your folder as an unstaged, newly added file.

---

## Summary Table

| Command                               | What it does                                            |
|---------------------------------------|---------------------------------------------------------|
| git rm file1.txt                      | Removes file from working directory and stages deletion |
| git status -s                         | Shows file as staged for deletion (`D file1.txt`)       |
| git commit -m "Delete file1.txt"      | Records the deletion in your project's history          |
| git restore --source=HEAD~1 file1.txt | Restores the file from the previous commit              |

---