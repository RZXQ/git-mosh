# Squash Merging Workflow & Notes

## Steps

1. **Switch to a new feature/bugfix branch**
    ```bash
    git switch bug
    ```

2. **Edit a file and commit changes**
    ```bash
    vi text.txt
    git commit -am "Fix issue part 1"
    ```

3. **Edit again and commit another change**
    ```bash
    vi text.txt
    git commit -am "Fix issue part 2"
    ```

4. **Switch back to main**
    ```bash
    git switch main
    ```

5. **Merge with squash (combine commits into one)**
    ```bash
    git merge --squash bug
    ```

6. **Commit the squashed changes as one commit**
    ```bash
    git commit -am "Squash commit: fix issue from bug branch"
    ```

---

## Why Use `--squash`?

- ✅ **Keeps the main branch history clean**  
  Only one commit is added to main, instead of many work-in-progress commits.

- ✅ **Readable project history**  
  Makes it easy to understand what changed and why, without excess noise.

- ✅ **Flexible local development**  
  You can commit freely on feature branches, then combine them for a tidy merge.

- 🚫 **Note:**  
  The original branch’s individual commit history is not preserved. Only the combined changes appear on main.

---

## Summary Table

| Command                  | Purpose                       |
|--------------------------|-------------------------------|
| git merge --squash bug   | Prepare a squash merge        |
| git commit -am "message" | Create single squashed commit |
| git log                  | View clean commit history     |

---

**Tip**:  
Use squash merging when you want to bring in the results of a branch as a single logical change, rather than preserving
the full commit-by-commit process.