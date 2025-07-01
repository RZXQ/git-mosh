# Initial Commit — Setting Up the Project Foundation

## Commit Command

```bash
git commit -m "initial commit"
```

- This command creates the very first commit in your Git repository, often called the "initial commit."
- The `-m` flag provides a short commit message directly in the command line.

---

## Example of a Longer Commit Description

For extra clarity, you can provide a longer commit message (with details) by omitting the `-m` and letting an editor
open, or by using multiple `-m` flags (the first for the subject line, the second for the body):

```bash
git commit -m "initial commit" -m "This commit establishes the basic project structure and initial files
- Added core project files
- Set up initial configuration
- Created basic directory structure"
```

### Typical "Initial Commit" Message Structure

- **Short summary:**  
  `initial commit`
- **Long description:**
  ```
  This commit establishes the basic project structure and initial files
  - Added core project files
  - Set up initial configuration
  - Created basic directory structure
  ```

---

## Summary Table

| Command Example                                                  | Description                                             |
|------------------------------------------------------------------|---------------------------------------------------------|
| `git commit -m "initial commit"`                                 | Short subject line (the most common for initial commit) |
| `git commit -m "initial commit" -m "Longer description here..."` | Subject + detailed description                          |

---

**Tip:**

- The initial commit sets up your repository for future tracking and collaboration.
- It's good practice to document what you established in this first commit!