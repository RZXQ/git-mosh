# Using `git log` to See the History of a File

The `git log` command can show the history of changes for a specific file.  
Below are examples with explanations.

---

## 1. See All Commits That Touched a File

```bash
git log toc.txt
```

- Shows all commits that modified `toc.txt`.
- Includes full commit details (author, date, message, and diff).

---

## 2. Compact List of Commits for a File

```bash
git log --oneline toc.txt
```

- Shows a simple, one-line-per-commit history for `toc.txt`.
- Example output:
    ```
    50db987 Include the first section in TOC.
    a642e12 Add header to all pages.
    ...
    ```
- Quick way to see when the file changed and by whom.

---

## 3. Show File History with Stats

```bash
git log --oneline --stat toc.txt
```

- Includes a compact commit list and, for each commit, a short summary of what changed (number of insertions/deletions).
- Example output:
    ```
    50db987 Include the first section in TOC.
     toc.txt | 2 ++
    a642e12 Add header to all pages.
     toc.txt | 1 +
    ...
    ```
- Useful to see how much was changed in each commit.

---

## 4. Show File History with Patches (Diffs)

```bash
git log --oneline --patch toc.txt
```

- For each commit that touched `toc.txt`, shows a one-line summary and the full patch (diff) for that commit.
- Lets you see exactly what was changed to `toc.txt` in each commit.

---

## Summary Table

| Command                           | What it does                                         |
|-----------------------------------|------------------------------------------------------|
| git log toc.txt                   | Shows all commits that changed toc.txt (full detail) |
| git log --oneline toc.txt         | Shows a simple list of commits for toc.txt           |
| git log --oneline --stat toc.txt  | List of commits + stats for toc.txt changes          |
| git log --oneline --patch toc.txt | List of commits + full diffs for toc.txt             |

---

**Tip:**  
Replace `toc.txt` with any file name to see its history!