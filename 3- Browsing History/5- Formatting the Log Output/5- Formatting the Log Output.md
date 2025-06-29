# Using `git log` with `--pretty=format:` and Common Placeholders

The `git log` command shows the commit history.  
The `--pretty=format:"..."` option lets you customize how each commit is shown.  
Below are examples with explanations and comments.

---

## 1. Basic Custom Message (No commit info)

```bash
git log --pretty=format:"hello"
```

- Shows the word "hello" for each commit entry.
- **No commit details are shown.**

---

## 2. Show Author Name and Commit Hash (Full)

```bash
git log --pretty=format:"%an committed %H"
```

- `%an` = author name (who made the commit)
- `%H` = full commit hash (a long unique ID for the commit)
- Example output:
    ```
    Alice committed f4c3b2a1d9e5c1234567890abcdef1234567890a
    ```

---

## 3. Show Author Name and Short Commit Hash

```bash
git log --pretty=format:"%an committed %h"
```

- `%h` = short commit hash (shorter version of the commit ID)
- Example output:
    ```
    Alice committed f4c3b2a
    ```

---

## 4. Show Author Name, Short Hash, and Commit Date

```bash
git log --pretty=format:"%an committed %h on %cd"
```

- `%cd` = commit date (when the commit was made)
- Example output:
    ```
    Alice committed f4c3b2a on Mon Jun 29 10:59:22 2025 +0000
    ```

---

## 5. Colorize Author Name

```bash
git log --pretty=format:"%Cgreen%an committed %h on %cd"
```

- `%Cgreen` = start green color (for terminal display)
- `%an` = author name (will appear in green)
- `%Creset` = resets color to normal (not used here, but see next example)
- Example output:
    ```
    [author name in green] committed f4c3b2a on Mon Jun 29 10:59:22 2025 +0000
    ```

---

## 6. Colorize Author Name, Reset Color for Rest

```bash
git log --pretty=format:"hello %Cgreen%an%Creset committed %h %cd"
```

- `hello` = literal word at the start of each line
- `%Cgreen` = start green color
- `%an` = author name (in green)
- `%Creset` = reset color to default (rest of line is normal color)
- `%h` = short commit hash
- `%cd` = commit date
- Example output:
    ```
    hello [author name in green] committed f4c3b2a Mon Jun 29 10:59:22 2025 +0000
    ```

---

## Summary of Placeholders

| Placeholder | What it shows                               |
|-------------|---------------------------------------------|
| %an         | Author name                                 |
| %H          | Full commit hash (long)                     |
| %h          | Short commit hash                           |
| %cd         | Commit date                                 |
| %Cgreen     | Start green color in output (terminal only) |
| %Creset     | Reset color to normal                       |

---

**Tip:**  
You can combine these placeholders to create your own custom log format.  
Colors only show in a terminal that supports them.