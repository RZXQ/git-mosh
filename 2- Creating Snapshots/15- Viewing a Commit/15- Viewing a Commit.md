# Git `show` and `ls-tree` Command Examples with Comments

Below are some commonly used `git show` and `git ls-tree` commands, with detailed comments to help you understand what
each command does. This is especially useful if you're new to Git and want to understand the difference between showing
commits, files, and the structure of your repository.

---

## 1. Show Commit Details

```sh
# Show the details of the commit with hash 'abad544'
git show abad544

# If you type only a few characters of the hash and it's unambiguous, Git will find it for you
git show aba
```

- `git show <commit>` shows:
    - The commit message
    - Author and date
    - The diff (changes introduced by this commit)

---

## 2. Show Commits Relative to HEAD

```sh
# Show the most recent commit (HEAD points to the latest commit)
git show HEAD

# Show the previous commit (one before HEAD)
git show HEAD~1

# Show the commit two steps before HEAD
git show HEAD~2
```

- `HEAD` refers to your current branch tip (latest commit).
- `HEAD~1` is the parent (previous commit).
- `HEAD~2` is the grandparent (two commits back), etc.

---

## 3. Show a Specific File as It Was in a Commit

```sh
# Show the content of file1.txt as it was in the latest commit
git show HEAD:./file1.txt
```

- This will **output the full file content** as it existed at that commit.
- The syntax is: `git show <commit>:<path>`

---

## 4. List Files and Directories in a Commit (ls-tree)

```sh
# List all files and directories at the HEAD commit
git ls-tree HEAD

# List all files and directories at the previous commit
git ls-tree HEAD~1
```

- `git ls-tree` displays the **tree structure** (files and folders) at a specific commit.
- **Files** are shown as `blob` (content objects).
- **Directories** are shown as `tree` (they may contain more blobs/trees inside).

### Example Output:

```
100644 blob 33c5a0e...    file1.txt
100644 blob 7b8e1f0...    file2.txt
040000 tree d8e8fca...    src
```

- Here, `file1.txt` and `file2.txt` are **blobs** (files).
- `src` is a **tree** (directory).

---

## 5. Summary Table

| Command                  | What it shows                                         |
|--------------------------|-------------------------------------------------------|
| git show <commit>        | Commit details and diff                               |
| git show <commit>:<path> | File content at that commit                           |
| git ls-tree <commit>     | List of files (blobs) and folders (trees) at a commit |

---

## 6. Visual Explanation

- **`git show`**: Think of it as "show me the details of this commit (or file at a commit)".
- **`git ls-tree`**: Think of it as "show me the structure of the repository at a certain commit (files and folders)".

---

> **Tip:**
>
> - Use `git show` to see what changed in a commit or to view a file at a specific commit.
> - Use `git ls-tree` to explore the structure of your repository at any point in history.
