# Using `git blame` to See Who Changed Each Line of a File

The `git blame` command shows who last edited each line of a file, along with the commit information.

---

## 1. Basic Usage: See Who Changed Every Line

```bash
git blame audience.txt
```

- Shows, for every line in `audience.txt`:
    - Commit hash
    - Author
    - Date
    - The line content
- Example output:
    ```
    1ebb7a7e (Alice 2022-01-05 10:00:00 +0000  1) This is the audience section.
    fb0d184a (Bob   2022-01-06 11:15:32 +0000  2) Another line for the audience.
    ```

---

## 2. Show Author Email Addresses

```bash
git blame -e audience.txt
```

- Adds the author’s email address to each line’s annotation.
- Example output:
    ```
    1ebb7a7e (Alice <alice@example.com> 2022-01-05 10:00:00 +0000  1) This is the audience section.
    fb0d184a (Bob   <bob@example.com>   2022-01-06 11:15:32 +0000  2) Another line for the audience.
    ```

---

## 3. Limit Blame to Specific Line Numbers

```bash
git blame -L 1,3 audience.txt
```

- Limits the output to lines 1 through 3 of `audience.txt`.
- Useful when you only want to see who changed a specific part of a file.

---

## Summary Table

| Command                       | What it does                                  |
|-------------------------------|-----------------------------------------------|
| git blame audience.txt        | Shows who last changed each line of the file  |
| git blame -e audience.txt     | Shows blame with author email addresses       |
| git blame -L 1,3 audience.txt | Shows blame only for lines 1 to 3 of the file |

---

**Tip:**  
`git blame` is very useful for tracking down when and by whom a line was introduced or changed!