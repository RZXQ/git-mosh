# Working with Git Tags (Lightweight & Annotated) — With Example Outputs

This guide explains how to create, view, and manage tags in git, showing the actual output you would see at each step.

---

## 1. Create a Lightweight Tag at the Current Commit

```bash
git tag v1.0
```

- **What it does:**  
  Creates a simple tag named `v1.0` pointing to the current commit (`HEAD`).
- **No output** on success.

---

## 2. Create a Lightweight Tag for a Specific Commit

```bash
git tag v1.0 5e7a828
```

- **What it does:**  
  Creates (or moves) tag `v1.0` to point to commit `5e7a828`.  
  If a tag with the same name exists, this overwrites it (unless protected).

---

## 3. Example: Commit Log with Tag

After tagging, your `git log --oneline --decorate` might look like:

```
a642e12 (HEAD -> master) Add header to all pages.
50db987 Include the first section in TOC.
555b62e Include the note about committing after staging the changes.
91f7d40 Explain various ways to stage changes.
edb3594 (tag: v1.0) First draft of staging changes.
24e86ee Add command line and GUI tools to the objectives.
36cd6db Include the command prompt in code sample.
...
```

- `(tag: v1.0)` shows the tag on that commit.

---

## 4. Checkout a Tag

```bash
git checkout v1.0
```

- **What it does:**  
  Checks out the commit referenced by tag `v1.0` (detached HEAD state).
- **Example log after checkout:**
    ```
    a642e12 (master) Add header to all pages.
    50db987 Include the first section in TOC.
    555b62e Include the note about committing after staging the changes.
    91f7d40 Explain various ways to stage changes.
    edb3594 (HEAD, tag: v1.0) First draft of staging changes.
    24e86ee Add command line and GUI tools to the objectives.
    ...
    ```
- Notice `(HEAD, tag: v1.0)` indicates HEAD is now at the tagged commit.

---

## 5. List All Tags

```bash
git tag
```

- **Shows:**
    ```
    v1.0
    v1.1
    ```
- Lists all tags in alphabetical order.

---

## 6. Create an Annotated Tag

```bash
git tag -a v1.1 -m "My Version 1.1"
```

- **What it does:**  
  Creates an annotated tag (`-a`) with a message.
- **No output** on success. Annotated tags store the tagger's name, email, and date.

---

## 7. List Tags With Messages

```bash
git tag -n
```

- **Shows:**
    ```
    v1.0   First draft of staging changes.   (commit message)
    v1.1   My Version 1.1                   (tag message)
    ```
- For annotated tags, the message is the tag message.
- For lightweight, it shows the commit message.

---

## 8. Show Tag Details

```bash
git show v1.1
```

- **Shows:**
    ```
    tag v1.1
    Tagger: Reacher <macryze@icloud.com>
    Date:   Mon Jun 30 16:08:42 2025 +0800

    My Version 1.1

    commit edb3594bfa5572d81e24b33aa928938e46907275 (HEAD, tag: v1.1, tag: v1.0)
    Author: Moshfegh Hamedani <moshfegh@live.com.au>
    Date:   Mon Aug 17 14:24:38 2020 -0700

        First draft of staging changes.

    diff --git a/sections/creating-snapshots/staging-changes.txt ...
    ```
- Shows tag info, tagger, date, message, and the referenced commit (with diff).

---

## 9. Delete a Tag

```bash
git tag -d v1.1
```

- **Shows:**
    ```
    Deleted tag 'v1.1' (was edb3594)
    ```
- Removes the tag from your local repository.

---

## Summary Table

| Command                               | Description                                           | Example Output                   |
|---------------------------------------|-------------------------------------------------------|----------------------------------|
| `git tag v1.0`                        | Create lightweight tag at current commit              | (no output)                      |
| `git tag v1.0 <commit>`               | Tag a specific commit                                 | (no output)                      |
| `git checkout <tag>`                  | Checkout the commit referenced by tag (detached HEAD) | See log, `(HEAD, tag: v1.0)`     |
| `git tag`                             | List all tags                                         | v1.0<br>v1.1                     |
| `git tag -a v1.1 -m "My Version 1.1"` | Create an annotated tag with message                  | (no output)                      |
| `git tag -n`                          | List tags with messages                               | v1.0 ... v1.1 ...                |
| `git show v1.1`                       | Show details about tag and referenced commit          | tag info, commit info, diff      |
| `git tag -d v1.1`                     | Delete tag from local repo                            | Deleted tag 'v1.1' (was edb3594) |

---

**Tip:**

- Use lightweight tags for quick references; use annotated tags for releases.
- Tags are just pointers—deleting a tag never deletes a commit!