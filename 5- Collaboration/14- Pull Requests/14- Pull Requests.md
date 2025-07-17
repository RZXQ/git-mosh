# GitHub Pull Request Collaboration Tutorial

This guide will walk you through the typical workflow for making changes in a feature branch, opening a pull request,
requesting a code review, addressing feedback, merging your changes, **and updating your local repository after merging
**.

---

## 1. Create a Feature Branch and Make Changes

**On Amy's local repository:**

``` bash
# Create and switch to a new branch called 'feature/login'
git switch -c feature/login
# Make your code changes
echo hello >> file3.txt
# Stage and commit the changes
git add . git commit -m "write hello to file3"
# Push the new branch to GitHub
git push -u origin feature/login
``` 

---

## 2. Open a Pull Request on GitHub

1. Go to your repository on GitHub.
2. Click the **"Pull requests"** tab, then click **"New pull request"**.
3. **Base:** Select `main`.  
   **Compare:** Select your feature branch (e.g., `feature/login`).
4. Fill in the title and description for your pull request.
5. Add a reviewer (e.g., select "Mosh" as reviewer).
6. Submit the pull request.

---

## 3. Review and Request Changes

**On the reviewer's (Mosh's) side:**

1. Go to the "Pull requests" tab and open the relevant pull request.
2. Review the code. You can comment on specific lines:
   > For example: "This line is good, but it's better if you capitalize the 'H' in Hello."
3. After commenting, click **"Start review"** (if leaving multiple comments).
4. Finish the review by clicking **"Submit review"** and select "Request changes".  
   Leave overall feedback (e.g., "Please make these changes and push again.").

---

## 4. Address Feedback and Update the Pull Request

**Back on Amy's local machine:**

``` bash
# Make the changes requested in the review
echo Hello > file3.txt
# Stage and commit the changes
git commit -am "capitalize Hello"
# Push the changes to update the pull request
git push
``` 

No need to create a new PR—your changes automatically appear in the existing pull request.

---

## 5. Approve and Merge the Pull Request

**On the reviewer's (Mosh's) side:**

1. Revisit the pull request.
2. Confirm that feedback was addressed.  
   Optionally, leave a comment: "Everything looks perfect!"
3. Click **"Approve"** to approve the changes.

**To merge:**

1. Click the **"Merge pull request"** button.
2. Confirm the merge.

---

## 6. Update Your Local Repository After the Merge

Now that your pull request is merged on GitHub, your local `main` branch does **not** yet have these latest changes.  
To sync your local repository with the updated remote `main` branch, run:

``` bash
# Switch to main, if not already there
git switch main
# Pull the latest changes from GitHub
git pull
``` 

Now your local repository is up-to-date with the merged changes.

---

## Summary

- Feature development happens in a separate branch.
- Pull requests are used to propose and review changes before merging to `main`.
- Reviewers can request changes or approve.
- Authors update the branch to address feedback; reviewers approve.
- Once approved, the pull request is merged.
- **After merging, all collaborators should pull the latest changes to their local `main` branch to stay up-to-date.**

```
