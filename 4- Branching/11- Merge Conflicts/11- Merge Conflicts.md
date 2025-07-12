## 1. Start a New Feature Branch

```bash
git switch -c bugfix/change-password
```

**Output:**

```plaintext
Switched to a new branch 'bugfix/change-password'
```

- Creates and switches to a new branch for fixing the password feature.

------

## 2. Make Changes and Commit

```bash
vi change-password.txt  # Edit the file
git add .
git commit -m "Update password requirements"
```

- Modifies the password policy documentation on the feature branch.

**Commit Graph:**

```plaintext
* 3a7f1c5 (HEAD -> bugfix/change-password) Update password requirements
| * 2b9e4d6 (main) Add security disclaimer
|/  
* 5c3d8f2 Initial commit with README
```

------

## 3. Switch Back to Main and Make Conflicting Changes

```bash
git switch main
vi change-password.txt  # Edit the same file
git add .
git commit -m "Update password format example"
```

- Modifies the same file on `main`, creating a conflict with the feature branch.

**Commit Graph:**

```plaintext
* 2b9e4d6 (HEAD -> main) Update password format example
| * 3a7f1c5 (bugfix/change-password) Update password requirements
|/  
* 5c3d8f2 Initial commit with README
```

------

## 4. Attempt to Merge (Conflict Occurs)

```bash
git merge bugfix/change-password
```

**Conflict Output:**

```plaintext
Auto-merging change-password.txt
CONFLICT (content): Merge conflict in change-password.txt
Automatic merge failed; fix conflicts and then commit the result.
```

- Git detects conflicting changes in `change-password.txt`.

**Status Check:**

```bash
git status -s
```

**Output:**

```plaintext
UU change-password.txt
```

- `UU` indicates an unmerged file.

------

## 5. Resolve the Conflict Manually

Edit `change-password.txt` to fix conflicts. The file will contain markers like:

```plaintext
<<<<<<< HEAD
Passwords must include at least one symbol.
=======
Passwords should be at least 12 characters long.
>>>>>>> bugfix/change-password
```

**Options:**

1. **Accept Current Change (`HEAD`)**: Keep the `main` version.
2. **Accept Incoming Change**: Use the feature branch version.
3. **Combine Both**: Merge both changes carefully.

**After Editing:**

```bash
git add change-password.txt
git status -s
```

**Output:**

```plaintext
M  change-password.txt
```

- `M` indicates the file is staged after conflict resolution.

------

## 6. Commit the Merge

```bash
git commit -m "Merge bugfix/change-password into main"
```

**Commit Graph:**

```plaintext
*   7d5f2e9 (HEAD -> main) Merge bugfix/change-password into main
|\  
| * 3a7f1c5 (bugfix/change-password) Update password requirements
* | 2b9e4d6 Update password format example
|/  
* 5c3d8f2 Initial commit with README
```

- The merge commit shows both parent histories.

------

## 7. Best Practices for Conflict Resolution

1. **Avoid Conflicts**:

    - Regularly merge `main` into feature branches.
    - Use clear commit messages and atomic changes.

2. **Resolve with Care**:

    - Understand both changes before combining them.
    - Test the merged code to ensure functionality.

3. **Visual Tools**:

   ```bash
   git mergetool  # Use a visual diff tool (e.g., VS Code, meld)
   ```

4. **Abort a Merge**:

   ```bash
   git merge --abort  # Undo the merge attempt
   ```

------

## Summary Table

| Command              | Purpose                              | Example Output              |
|----------------------|--------------------------------------|-----------------------------|
| `git merge <branch>` | Merge a branch into current branch   | Conflict message or success |
| `git status -s`      | Check conflict status                | `UU` for unmerged files     |
| `git add <file>`     | Mark conflict as resolved            | `M` for staged file         |
| `git commit`         | Finalize the merge                   | Merge commit in history     |
| `git mergetool`      | Open visual conflict resolution tool | Launches GUI diff tool      |
| `git merge --abort`  | Cancel the merge process             | Reverts to pre-merge state  |

------

**Key Takeaways:**

- Merge conflicts happen when the same file is modified on different branches.
- Use `git status` to identify conflicting files.
- Edit files manually or use visual tools to resolve conflicts.
- Always test merged code before committing!