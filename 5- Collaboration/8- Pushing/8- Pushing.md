## Explained `git push origin main`

- **Purpose:**
  This command uploads your local changes from the `main` branch to the remote repository named `origin` (commonly on
  GitHub, GitLab, etc.).
- **Breakdown:**
    - **`git push`:** The basic command to upload commits from your local repository to a remote one.
    - **`origin`:** The default name Git assigns to the remote repository you cloned from or set up.
    - **`main`:** The name of the branch you want to update on the remote. (Older projects may use `master` instead.)

-

All commits on your local `main` branch that the remote doesn’t have will be sent to the remote repository’s `main`
branch. If pushing to a shared repo, others will see your new commits. **Effect:**

- **Useful when:**
    - You’re ready to share your latest work
    - Collaborating with teammates
    - Deploying or syncing code with a remote server

- **Example usage:**

``` bash
  git push origin main
```
