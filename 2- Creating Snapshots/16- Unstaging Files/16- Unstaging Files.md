# Unstaging Multiple Files in Git

When you use Git, sometimes you might accidentally add files to the staging area (with `git add`). If you want to remove
them from the staging area (unstage), you can use the `git restore --staged` command.

---

## 1. Check the Status of Your Files

```bash
git status -s
```

- This command shows a short summary of the current status of your files.
- Files with `A` are newly added (staged for commit).
- Files with `M` are modified.
- Files with `??` are untracked (not in the repository).

---

## 2. Unstage a Single File

```bash
git restore --staged file1.txt
```

- This command removes `file1.txt` from the staging area.
- The file is not deleted or changed in your working directory. It just won’t be included in the next commit.

---

## 3. Unstage Multiple Files at Once

```bash
git restore --staged file1.txt file2.txt
```

- This command removes both `file1.txt` and `file2.txt` from the staging area at the same time.
- Again, the files are not deleted or changed in your working directory.

---

## How Does `git restore --staged` Work?

- The **staging area** is like a waiting area for files you want to include in your next commit.
- The **repository** is where your last committed (saved) version of files lives.

When you use `git restore --staged`:

- Git looks at the last committed version of the file in the repository.
- It copies that version over the version in the staging area.
- If the file was **already in the repository**, it reverts the staged changes back to the last saved version.
- If the file was **newly added** (status `A`), there is no version in the repository yet. So, Git simply removes it
  from the staging area, and it becomes **untracked** (status `??`).

---

### Example: New File

1. You create `file2.txt` and add it with `git add file2.txt`.  
   Now, `git status -s` shows:
   ```
   A  file2.txt
   ```
2. You run:
   ```bash
   git restore --staged file2.txt
   ```
   Now, `file2.txt` is **no longer staged**. It becomes **untracked** (just like a new file you haven’t added yet).

---

**Summary:**

- `git restore --staged <file>` removes a file from the staging area.
- If the file was new, it becomes untracked.
- If the file was already tracked and modified, the changes stay in your working folder, but the staging area is reset.

---