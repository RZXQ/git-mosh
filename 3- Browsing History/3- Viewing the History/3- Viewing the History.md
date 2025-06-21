## 1. `git log --oneline`

Shows a **simple list of commits**—one brief line per commit (short hash + commit message).
**Example:**

``` bash
git log --oneline
```

**Output:**

``` 
a1b2c3d Fix typo in README
e4f5g6h Add login feature
i7j8k9l Initial commit
```

- **Use this:** For a quick summary of your recent commits.

## 2. `git log --oneline --reverse`

Shows a one-line list of commits but starts with the **oldest commit first**.
**Example:**

``` bash
git log --oneline --reverse
```

**Output:**

``` 
i7j8k9l Initial commit
e4f5g6h Add login feature
a1b2c3d Fix typo in README
```

- **Use this:** To see your project's commit history from the beginning.

## 3. `git log --oneline --stat`

Shows each commit in the simple one-line style, then lists which files changed and how many lines were added/removed for
each commit.
**Example:**

``` bash
git log --oneline --stat
```

**Output:**

``` 
a1b2c3d Fix typo in README
 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
e4f5g6h Add login feature
 login.js  | 10 ++++++++++
 1 file changed, 10 insertions(+)
```

- **Use this:** To easily see both the commit summary and a quick summary of what was changed in each one.

## 4. `git log --stat`

Displays detailed commit info (full hash, author, date, full message) plus file change stats for each commit.
**Example:**

``` bash
git log --stat
```

**Output:**

``` 
commit a1b2c3d4e5f6g7h
Author: Your Name <your.email@example.com>
Date:   Wed Jun 19 15:29:31 2024 +0800

    Fix typo in README

 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

- **Use this:** When you want to see who made changes, when, their message, and details about which files were altered.

## 5. `git log --oneline --patch`

Shows each commit in one line, followed by the **full code diff** (the actual code added or removed).
**Example:**

``` bash
git log --oneline --patch
```

**Output:**

``` 
a1b2c3d Fix typo in README
diff --git a/README.md b/README.md
index 39e86c2..cb9849e 100644
--- a/README.md
+++ b/README.md
@@ -1,5 +1,5 @@
-This is the README
+This is the Readme
```

- **Use this:** To see the summary and the exact changes made in one view.

## Summary Table

| Command                       | Description                           | Output style          | Shows code diff? | Shows file stats? | One-line summary? |
|-------------------------------|---------------------------------------|-----------------------|------------------|-------------------|-------------------|
| `git log --oneline`           | Short summaries, newest first         | 1 line per commit     | No               | No                | Yes               |
| `git log --oneline --reverse` | Short summaries, oldest first         | 1 line per commit     | No               | No                | Yes               |
| `git log --oneline --stat`    | One-liners + file stats               | 1 line + file stats   | No               | Yes               | Yes               |
| `git log --stat`              | Detailed commit info + file stats     | Multi-line per commit | No               | Yes               | No                |
| `git log --oneline --patch`   | One-liner + full code changes (diffs) | 1 line + code diff    | Yes              | Sometimes*        | Yes               |

* With , line counts may be shown at the end of the change details. `--patch`

## Key Points

- **`--oneline`**: Keeps things short and simple—great for quick history scans.
- **`--stat`**: Adds a summary of what files changed and how many lines.
- **`--patch`**: Adds the actual code difference for each commit.
- **`--reverse`**: Flips the order, so oldest commits come first.
