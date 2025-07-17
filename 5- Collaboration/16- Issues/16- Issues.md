## Issues

- **Linked Pull Requests:**

  When working with issues in a repository, you can link pull requests (PRs) to those issues by referencing them in the
  PR description or commit messages using keywords like `closes #123`, `fixes #123`, or `resolves #123` (where `123` is
  the issue number).

  Once a PR is linked to an issue, GitHub automatically displays the connection in the issue sidebar under “Linked Pull
  Requests.” This visual association helps everyone on the team see which branches or pull requests are intended to
  solve a particular problem or new feature request.

  **Why use linked pull requests?**
    - They make project tracking easier—you can quickly tell if work is in progress or has been completed for an issue.
    - When the linked pull request is merged, GitHub will automatically close the referenced issue if you used closing
      keywords.
    - Reviewers can navigate between the issue discussion and the PR implementation with a single click, improving
      coordination between planning and code changes.

  **Example:**

  If you have an open issue for a bug (`#42`), and you open a PR with the description:
  ```bash
  Fix the typo in widget rendering

  Closes #42
  ```
    - GitHub will automatically associate and show this pull request on the issue page.
    - When the PR is merged, issue #42 will be closed.

  **Summary:**  
  Linking pull requests to issues improves traceability, documentation, and team awareness throughout the development
  process.