### List Branches Already Merged Into the Current Branch

``` bash
git branch --merged
```

- **Shows all local branches that have been fully merged into your current branch.**
- These branches are usually safe to delete.

**Sample Output:**

``` 
  feature/navbar
  feature/cleanup
* main
```

_(main and the two features have all their commits in your current branch)_

### List Branches Not Yet Merged Into the Current Branch

``` bash
git branch --no-merged
```

- **Shows all local branches that have commits NOT yet merged into your current branch.**
- These may contain unique work that isn’t yet incorporated.

**Example Output:**

``` 
  feature/login
  feature/dashboard
```

_(login and dashboard are not fully merged into the current branch)_

### Common Usage

1. **To safely delete fully merged branches:**

``` bash
    git branch --merged
    git branch -d branch_name
```

1. **To check what’s still outstanding before merging or cleaning up:**

``` bash
    git branch --no-merged
```

## Quick Reference Table

| Command                | Shows                               | When to Use                     |
|------------------------|-------------------------------------|---------------------------------|
| git branch --merged    | Branches merged into current branch | Safe cleanup                    |
| git branch --no-merged | Branches NOT yet merged             | Find incomplete or WIP branches |

Always double-check before deleting branches so you don’t lose work that hasn’t been integrated! **Tip:**
`git branch --no-merged`
Let me know if you want diagrams or scenarios to illustrate this in project workflows.
