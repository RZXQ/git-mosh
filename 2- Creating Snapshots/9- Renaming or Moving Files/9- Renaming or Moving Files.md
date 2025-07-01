# Renaming Files in Git: Manual and Git-Integrated Methods

This guide explains how to rename files in a Git repository, both with system commands and with Git's built-in rename
command.

---

## 1. Rename a File Using System Command

```bash
mv file1.txt main.js
```

- Renames `file1.txt` to `main.js` on the filesystem.
- From Git’s perspective, this looks like you deleted `file1.txt` and created a new, untracked `main.js`.

---

## 2. Stage the Deletion and Addition

```bash
git add file1.txt
git add main.js
```

- `git add file1.txt`: Stages the removal of the old file.
- `git add main.js`: Stages the new file for tracking.
- **Git is smart:** When you commit both actions together, Git usually recognizes this as a rename (
  `renamed: file1.txt -> main.js`) if the content of the files is mostly unchanged.

---

## 3. Rename a File Using Git's Built-In Command

```bash
git mv main.js file1.js
```

- Renames `main.js` to `file1.js` in the working directory and stages the change.
- Both the filesystem and Git's index are updated in one step.

---

## 4. Commit the Rename Operations

```bash
git commit -m "Refactor code."
```

- Records all the rename operations in your project history.
- The commit will show file renames (not just deletions and additions).

---

## Summary Table

| Command                        | What it does                                            |
|--------------------------------|---------------------------------------------------------|
| mv file1.txt main.js           | Rename file in the filesystem (not recorded by Git yet) |
| git add file1.txt              | Stage the deletion of the old file                      |
| git add main.js                | Stage the addition of the new file                      |
| git mv main.js file1.js        | Rename and stage the file in one step using Git         |
| git commit -m "Refactor code." | Commit all staged changes, including renames            |

---

**Tip:**

- `git mv` is the preferred way to rename files, as it updates both the working directory and staging area in a single
  step!
- Even when using plain `mv`, Git will detect renames when you stage and commit both the deletion and addition together,
  as long as file content is similar.