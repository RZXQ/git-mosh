# Using `git shortlog` to Summarize Contributions

The `git shortlog` command provides a summary of commits grouped by author.  
It is useful for seeing who made how many commits in a repository.

---

## 1. Basic Usage

```bash
git shortlog
```

- Shows a summary of commits, grouped by author.
- Output example:
    ```
    Alice
         Add feature X
         Fix bug Y

    Bob
         Initial commit
         Refactor code
    ```
- Each author’s name is listed once, with their commit messages indented below.

---

## 2. Show Number of Commits per Author

```bash
git shortlog -n
```

- `-n` sorts the output by number of commits, most commits first.
- Output example:
    ```
       10  Alice
        5  Bob
    ```
- Only the author and the number of commits (no commit messages).

---

## 3. Show Only Number and Author (Suppress Messages)

```bash
git shortlog -s
```

- `-s` (summary) shows only the number of commits and the author's name.
- Output example:
    ```
        8  Alice
        3  Bob
    ```

---

## 4. Show Email Addresses Too

```bash
git shortlog -n -s -e
```

- `-e` includes email addresses next to author names.
- Output example:
    ```
       10  Alice <alice@example.com>
        5  Bob <bob@example.com>
    ```

---

## Summary Table

| Command               | What it does                                                            |
|-----------------------|-------------------------------------------------------------------------|
| git shortlog          | Shows commits grouped by author, with messages                          |
| git shortlog -n       | Sorts by number of commits per author                                   |
| git shortlog -s       | Shows only the count and author name (no messages)                      |
| git shortlog -n -s -e | Shows commit count, sorts by count, and includes author email addresses |

---

**Tip:**  
Use `git shortlog -n -s -e` for a quick overview of who contributed the most, including their email addresses.