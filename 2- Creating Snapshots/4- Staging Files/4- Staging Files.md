# Step-by-Step: Initialize a New Git Repository and Stage Files

This guide walks you through initializing a Git repository, viewing hidden files, creating and staging files, and
understanding the staging workflow.

---

## 1. Initialize a New Git Repository

```bash
git init
```

- Creates a hidden `.git` folder in the current directory, enabling version control.

---

## 2. List All Files (Including Hidden Files)

```bash
ls -a
```

- The `-a` flag shows all files, including hidden ones like `.git` that start with a dot.

---

## 3. Create New Text Files

```bash
echo hello > file1.txt
echo hello > file2.txt
```

- The `>` operator creates new files or overwrites existing ones with the text "hello".

---

## 4. Check the Status of Your Repository

```bash
git status
```

- Displays:
    - Untracked files
    - Modified files
    - Staged changes

---

## 5. Staging Workflow — Adding Files to the Staging Area

### Method 1: Add Specific Files Individually

```bash
git add file1.txt file2.txt
```

- Stages `file1.txt` and `file2.txt` for the next commit.

### Method 2: Add Files Using Wildcards

```bash
git add *.txt
```

- Stages all `.txt` files in the current directory.

### Method 3: Add All Changes (New, Modified, Deleted Files)

```bash
git add .
```

- The dot (`.`) represents the current directory and all subdirectories.
- Stages all changes (new, modified, and deleted files).

---

## 6. Modify an Existing File

```bash
echo world >> file1.txt
```

- The `>>` operator appends "world" to `file1.txt` instead of overwriting it.

---

## 7. Re-Stage the Modified File

```bash
git add file1.txt
```

- If a file is changed after being staged, it must be staged again to include the new changes.
- Git tracks the exact state of files when they're staged.

---

**Summary Table**

| Command                     | Description                                   |
|-----------------------------|-----------------------------------------------|
| git init                    | Initialize a new Git repository               |
| ls -a                       | List all files, including hidden ones         |
| echo hello > file.txt       | Create a new file with content                |
| git status                  | Show current working directory/staging status |
| git add file1.txt file2.txt | Stage specific files                          |
| git add *.txt               | Stage all .txt files                          |
| git add .                   | Stage all changes in repo                     |
| echo world >> file1.txt     | Append content to an existing file            |
| git add file1.txt           | Re-stage a modified file                      |

---