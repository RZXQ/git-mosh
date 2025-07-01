# Appending to a File and Committing Changes Quickly in Git

This short guide explains how to append text to a file, stage all changes, and commit in one step.

---

## 1. Append Text to a File

```bash
echo test >> fil1.txt
```

- Appends the text `test` to `fil1.txt`.
- If `fil1.txt` doesn't exist, this command creates it.

---

## 2. Commit All Modified Files in One Command

```bash
git commit -a -m "message"
```

or shorthand:

```bash
git commit -am "message"
```

- `-a` stages all modified and deleted tracked files (but **not** new untracked files).
- `-m "message"` specifies the commit message.
- Effectively: Stage all changes to tracked files and commit in one step.

---

**Note:**

- New files (untracked) must be added with `git add` before `git commit -a` will include them.