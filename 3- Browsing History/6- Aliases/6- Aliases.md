# Using Git Aliases for Shortcuts

Git allows you to create aliases (shortcuts) for longer commands.  
By setting an alias, you can type a short command instead of the full one.  
`--global` means the alias will be available in all your repositories.

---

## 1. Set a Custom Log Alias

```bash
git config --global alias.lg "log --pretty --pretty=format='%an committed %h'"
```

- This creates a new alias called `lg`.
- Now, you can use `git lg` to quickly see a log of commits showing:
    - The author name (`%an`)
    - The word `committed`
    - The short commit hash (`%h`)
- **This setting affects all your git repositories.**

---

## 2. Edit Your Global Git Config File

```bash
git config --global -e
```

- Opens your global `.gitconfig` file in your default text editor.
- You can see, edit, or remove your aliases and other settings here.

---

## 3. Using Your New Alias

```bash
git lg
```

- This runs the shortcut you set above.
- **Example output:**
    ```
    Alice committed 9f1e3ab
    Bob committed 8a912f2
    ```

---

## 4. Unstage All Files with an Alias

```bash
git config --global alias.unstage "restore --staged ."
```

- This creates an alias called `unstage`.
- Now, you can run `git unstage` to remove **all files** from the staging area (they won't be included in the next
  commit, but your changes remain in your working directory).
- It is a quick way to unstage everything at once.

---

## Summary Table

| Command / Alias        | What it does                                         |
|------------------------|------------------------------------------------------|
| git lg                 | Shows a custom log with author and short commit hash |
| git config --global -e | Edit your global git settings and aliases            |
| git unstage            | Unstages all files currently in the staging area     |

---

**Tip:**  
Aliases save time and typing, especially for frequently-used or long commands!