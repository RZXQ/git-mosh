# Using `git diff` to Compare Commits and File Changes

The `git diff` command shows the differences (changes) between commits, branches, or your working directory.
Here are some examples with explanations:

---

## 1. Compare All Changes Between Two Commits

```bash
git diff HEAD~2 HEAD
```

- Shows all the changes made between the commit two steps before the latest (`HEAD~2`) and the latest commit (`HEAD`).
- Displays the line-by-line differences for all affected files.

---

## 2. Compare Changes for a Specific File

```bash
git diff HEAD~2 HEAD file.txt
```

- Shows only the changes in `file.txt` between `HEAD~2` and `HEAD`.
- Useful if you want to see how a single file evolved over those commits.

---

## 3. List Only the Names of Changed Files

```bash
git diff HEAD~2 HEAD --name-only
```

- Lists the names of all files that were changed between these two commits.
- Does not show the actual content changes, just the filenames.

---

## 4. List File Names and Their Change Status

```bash
git diff HEAD~2 HEAD --name-status
```

- Lists the files changed and their status:
    - `A` = Added
    - `M` = Modified
    - `D` = Deleted
- Example output:
    ```
    M       file1.txt
    A       newfile.txt
    D       oldfile.txt
    ```

---

## Summary Table

| Command                            | What it does                                            |
|------------------------------------|---------------------------------------------------------|
| git diff HEAD~2 HEAD               | Shows all line-by-line changes between two commits      |
| git diff HEAD~2 HEAD file.txt      | Shows changes for only file.txt between the two commits |
| git diff HEAD~2 HEAD --name-only   | Lists names of files changed between the two commits    |
| git diff HEAD~2 HEAD --name-status | Lists file names and their change status (A/M/D)        |

---