# Comparing Branches and Viewing Differences in Git

This guide shows how to compare branches, view unique commits, and see file changes between branches, with example
outputs.

---

## 1. See Commits Unique to a Branch

### Commits in `bugfix/signup-form` that are not in `master`:

```bash
git log master..bugfix/signup-form
```

**Output:**

```
commit 05d3fdc8e58794b3fe9902ab45bd90b3b339743f (bugfix/signup-form)
Author: Reacher <macryze@icloud.com>
Date:   Tue Jul 1 09:52:32 2025 +0800

    Fix the bug that prevented the users from signing up.
```

#### Show these commits in one-line format:

```bash
git log master..bugfix/signup-form --oneline
```

**Output:**

```
05d3fdc (bugfix/signup-form) Fix the bug that prevented the users from signing up.
```

---

## 2. See the Diff Between Two Branches

```bash
git diff master..bugfix/signup-form
```

**Output:**

```
diff --git a/audience.txt b/audience.txt
index 4cfef55..00be59c 100644
--- a/audience.txt
+++ b/audience.txt
@@ -1,4 +1,3 @@
-AUDIENCE
-
+WHO TEIS COURSE IS FOR
+======================
 This course is for anyone who wants to learn Git.
-No prior experience is required.
\ No newline at end of file
```

- Shows all changes made in `bugfix/signup-form` that are not in `master`.

---

## 3. Diff with a Branch (from Current Branch)

### If you are on `master`, compare with `bugfix/signup-form`:

```bash
git diff bugfix/signup-form
```

- Shows what would change if you switched to `bugfix/signup-form` from your current branch (`master`).

---

## 4. Show Which Files Are Different

```bash
git diff --name-status bugfix/signup-form
```

**Output:**

```
M       audience.txt
```

- `M` = modified, `A` = added, `D` = deleted

#### Show Only File Names That Differ

```bash
git diff --name-only bugfix/signup-form
```

**Output:**

```
audience.txt
```

---

## Summary Table

| Command                                      | Description                                              | Example Output |
|----------------------------------------------|----------------------------------------------------------|----------------|
| git log master..bugfix/signup-form           | Commits in bugfix/signup-form not in master              | commit ...     |
| git log master..bugfix/signup-form --oneline | Same as above, one line per commit                       | 05d3fdc ...    |
| git diff master..bugfix/signup-form          | Shows all code differences between the branches          | diff ...       |
| git diff bugfix/signup-form                  | Shows diff between current branch and bugfix/signup-form | diff ...       |
| git diff --name-status bugfix/signup-form    | Shows which files were changed, and how (M/A/D)          | M audience.txt |
| git diff --name-only bugfix/signup-form      | Shows only the names of changed files                    | audience.txt   |

---

**Tip:**  
Use these commands to review feature branches before merging, or to see what’s unique about a branch!