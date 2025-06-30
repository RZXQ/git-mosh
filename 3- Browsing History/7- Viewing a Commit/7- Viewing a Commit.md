# Using `git show` to View Commits and File Changes

The `git show` command displays information about commits, including the changes made and which files were affected.  
Below are examples with comments explaining what each command does.

---

## 1. Show a Specific Commit

```bash
git show 921a2ff
```

- Shows detailed information about the commit with hash `921a2ff`.
- Includes the commit message, author, date, and the changes made (diff) in that commit.

---

## 2. Show the Latest Commit

```bash
git show HEAD
```

- Shows details of the most recent (latest) commit on the current branch.

---

## 3. Show an Older Commit (2 Steps Back)

```bash
git show HEAD~2
```

- Shows details of the commit that is two commits before the current one.
- `HEAD~2` means "go back 2 commits from HEAD".

---

## 4. Show the Content of a File as It Was in an Older Commit

```bash
git show HEAD~2:./file1.txt
```

- Shows the contents of `file1.txt` as it was in the commit two steps before the latest (HEAD~2).
- Useful for viewing or recovering the previous version of a file.

---

## 5. Show Only the File Names Changed in an Older Commit

```bash
git show HEAD~2 --name-only
```

- Shows the commit info and a list of only the file names that were changed in that commit.
- Does **not** show the full diff.

---

## 6. Show File Names and Their Change Status

```bash
git show HEAD~2 --name-status
```

- Shows the commit info, file names, and the type of change for each file.
    - `A` = Added
    - `M` = Modified
    - `D` = Deleted

- Example output:
    ```
    A       newfile.txt
    M       file1.txt
    D       oldfile.txt
    ```

---

## Summary Table

| Command                       | What it does                                          |
|-------------------------------|-------------------------------------------------------|
| git show 921a2ff              | Show details and changes of commit 921a2ff            |
| git show HEAD                 | Show details and changes of the latest commit         |
| git show HEAD~2               | Show details and changes of the commit two steps back |
| git show HEAD~2:./file1.txt   | Show contents of file1.txt at that earlier commit     |
| git show HEAD~2 --name-only   | List only the names of files changed in that commit   |
| git show HEAD~2 --name-status | List file names and type of change (A/M/D)            |

---