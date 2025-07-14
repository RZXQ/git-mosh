## 🟢 Start: Initial setup on `main`

``` bash
ls
# Output:
audience.txt  index.js  toc.txt

git log --oneline -s
# Output:
# (Shows short history of commits, if any)
```

## 🍃 Step 1: Create a Feature Branch

``` bash
git switch -c feature/shopping-card
# Output:
Switched to a new branch 'feature/shopping-card'
```

**Explanation:**
Creates and switches to a new branch called `feature/shopping-card` for your independent work.

## 📦 Step 2: Add a New File & Commit

``` bash
echo hello >> cart.txt
git add .
git commit -am "add cart.txt"
# Output:
[feature/shopping-card d72c54e] add cart.txt
1 file changed, 1 insertion(+)
create mode 100644 cart.txt
```

**Explanation:**
You added a new file and committed it. History of this branch is now ahead of `main`.

## 🔄 Step 3: Switch Back to `main` & make changes

``` bash
git switch main
echo hello >> toc.txt

git add .
git commit -am "update toc.txt"
# Output:
[main 613d3e8] update toc.txt
1 file changed, 1 insertion(+)
```

**Explanation:**
You made a parallel update to in `main`. Now both `main` and your feature branch have diverged. `toc.txt`

## ⬆️ Step 4: Bring `feature/shopping-card` up-to-date (Rebase)

``` bash
git switch feature/shopping-card
git rebase main
# Output:
Successfully rebased and updated refs/heads/feature/shopping-card.
```

**What is happening?**

- **Rebase** takes new commits from `main` and applies your `feature/shopping-card` changes _on top of_ them.
- This avoids a “merge commit” and keeps history cleaner and linear.

## 🔀 Step 5: Merge Back to `main`

``` bash
git switch main
git merge feature/shopping-card
# Output:
Updating 613d3e8..a1e526b
Fast-forward
cart.txt | 1 +
1 file changed, 1 insertion(+)
create mode 100644 cart.txt
```

**Explanation:**
Since `feature/shopping-card` was rebased onto `main`, the merge is “fast-forward”—no conflicts nor merge commit. All
history is linear.

## 📝 Step 6: More Changes—Potential for Conflict

1. You made new changes on both branches, risking conflict in : `toc.txt`

``` bash
echo ocean >> toc.txt
git commit -am "main -> ocean"
# On main branch

# --- Switch to 'feature' branch ---
git switch feature/shopping-card
echo mountain >> toc.txt
git commit -am "feature -> mountain"
# Now, toc.txt has diverging content in both branches
```

## ⚡️ Step 7: Rebasing Again—with Conflicts

``` bash
git rebase main
# Output:
Auto-merging toc.txt
CONFLICT (content): Merge conflict in toc.txt
error: could not apply e814cd6... feature -> mountain
hint: Resolve all conflicts manually...
```

**Explanation:**

- Both `main` and your feature branch changed since last sync. `toc.txt`
- Git cannot auto-merge; it asks you to _resolve the conflict_ manually.

## 🛠 Step 8: Resolve Conflict & Continue

1. Edit the conflicted file () using your preferred editor. `toc.txt`
2. Stage the file:

``` bash
git add toc.txt
```

1. Continue rebasing:

``` bash
git rebase --continue
# Output:
Successfully rebased and updated refs/heads/feature/shopping-card.
```

**If you were forced to commit manually (e.g., `git commit -m "merge conflicts"`), this adds a merge resolution commit.
**

## 🏁 Step 9: Final Merge Back to main

``` bash
git switch main
git merge feature/shopping-card
# Output:
Updating 8821e09..b5d2f88
Fast-forward
toc.txt | 2 +-
1 file changed, 1 insertion(+), 1 deletion(-)
```

# 🟦 Key Takeaways: What is Rebasing?

- **Rebasing** moves your branch to the tip of another (usually the base branch, e.g., `main`), applying your changes
  after the latest base updates.
- Maintains a clean, linear project history.
- Conflicts must be resolved _during_ the rebase, not at merge.
- After rebasing and merging, there are _no merge commits_—just a tidy, fast-forward history.

## 📋 Typical Outputs

- `Successfully rebased and updated refs/heads/branchname.` — Successful rebase, no conflicts.
- `CONFLICT (content): Merge conflict in filename` — Manual intervention needed.
- `Fast-forward` — The branch could be updated without a merge commit.

## 🧭 Clean Rebase Workflow (Summary Table)

| Action                      | Command                                  | Effect & What to Expect       |
|-----------------------------|------------------------------------------|-------------------------------|
| New Feature Branch          | `git switch -c feature/X`                | Start work separate from main |
| Sync w/Latest Main (rebase) | `git rebase main`                        | Replays your changes on top   |
| Handle Conflicts (if any)   | Edit, `git add`, `git rebase --continue` | Resolve, then continue rebase |
| Merge Feature into Main     | `git merge feature/X`                    | Fast-forward if up-to-date    |
