# git pull --rebase

This command fetches changes from the remote branch and then re-applies your local changes "on top" of those updates.  
It avoids creating unnecessary merge commits and results in a cleaner, linear history.

**Usage:**

```
bash git pull --rebase
``` 

**Effect:**

1. Updates your local branch with the latest changes from the remote.
2. Applies your local commits after the remote changes, instead of merging.

**Benefits:**

- Keeps project history clean and linear.
- Prevents extra merge commits.

**Tip:**  
Use this on your feature or topic branches before pushing your work to the repository.