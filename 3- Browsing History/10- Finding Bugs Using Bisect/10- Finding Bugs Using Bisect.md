# Using `git bisect` with Full `git log` Examples

This guide combines the bisect process with full sample `git log --oneline --all` outputs, so you can easily visualize
how `HEAD` moves through your commit history.

---

## 1. Start: Full Commit History

Before running bisect, here is the complete commit log:

```
a642e12 (master) Add header to all pages.
50db987 Include the first section in TOC.
555b62e Include the note about committing after staging the changes.
91f7d40 Explain various ways to stage changes.
edb3594 First draft of staging changes.
24e86ee Add command line and GUI tools to the objectives.
36cd6db Include the command prompt in code sample.
9b6ebfd Add a header to the page about initializing a repo.
fa1b75e Include the warning about removing .git directory.
dad47ed Write the first draft of initializing a repo.
fb0d184 Define the audience.
1ebb7a7 Define the objectives.
ca49180 Initial commit.
```

- Note: `(master)` shows the tip of the master branch; `HEAD` points here if you are on master.

---

## 2. Start Bisect

```bash
git bisect start
git bisect bad        # current commit (e.g., a642e12) is bad
git bisect good ca49180  # initial commit is good
```

After these commands, git checks out a commit in the middle for you to test.

---

## 3. After First Bisect Step: HEAD in the Middle

Suppose git checks out `36cd6db`. Your log might look like:

```
a642e12 Add header to all pages.
50db987 Include the first section in TOC.
555b62e Include the note about committing after staging the changes.
91f7d40 Explain various ways to stage changes.
edb3594 First draft of staging changes.
24e86ee Add command line and GUI tools to the objectives.
36cd6db (HEAD) Include the command prompt in code sample.
9b6ebfd Add a header to the page about initializing a repo.
fa1b75e Include the warning about removing .git directory.
dad47ed Write the first draft of initializing a repo.
fb0d184 Define the audience.
1ebb7a7 Define the objectives.
ca49180 Initial commit.
```

- Notice `(HEAD)` is now on `36cd6db`, not at the tip of master. You are in a "detached HEAD" state.

---

## 4. Mark Good/Bad and Continue

Suppose you test this commit and mark it as `good` or `bad`. Git checks out another commit to test:

```
a642e12 Add header to all pages.
50db987 Include the first section in TOC.
555b62e (HEAD) Include the note about committing after staging the changes.
91f7d40 Explain various ways to stage changes.
edb3594 First draft of staging changes.
24e86ee Add command line and GUI tools to the objectives.
36cd6db Include the command prompt in code sample.
9b6ebfd Add a header to the page about initializing a repo.
fa1b75e Include the warning about removing .git directory.
dad47ed Write the first draft of initializing a repo.
fb0d184 Define the audience.
1ebb7a7 Define the objectives.
ca49180 Initial commit.
```

---

## 5. Continue Bisecting

You continue to test and mark commits as `good` or `bad`. Each time, `HEAD` moves to a new commit in the middle of the
remaining range. For example:

```
a642e12 Add header to all pages.
50db987 (HEAD) Include the first section in TOC.
555b62e Include the note about committing after staging the changes.
91f7d40 Explain various ways to stage changes.
edb3594 First draft of staging changes.
24e86ee Add command line and GUI tools to the objectives.
36cd6db Include the command prompt in code sample.
9b6ebfd Add a header to the page about initializing a repo.
fa1b75e Include the warning about removing .git directory.
dad47ed Write the first draft of initializing a repo.
fb0d184 Define the audience.
1ebb7a7 Define the objectives.
ca49180 Initial commit.
```

---

## 6. Bisect Finds the First Bad Commit

When bisect finishes, it tells you which commit introduced the bug, e.g.:

```
555b62e1ebb92c97fc69910ad0981a7d6dbbf8c6 is the first bad commit
commit 555b62e1ebb92c97fc69910ad0981a7d6dbbf8c6
Author: Moshfegh Hamedani <moshfegh@live.com.au>
Date:   Mon Aug 17 14:26:49 2020 -0700

    Include the note about committing after staging the changes.

 sections/creating-snapshots/staging-changes.txt | 2 ++
 1 file changed, 2 insertions(+)
```

---

## 7. Reset Bisect and Return to Master

```bash
git bisect reset
```

Your log returns to normal, with HEAD at the tip of master:

```
a642e12 (HEAD -> master) Add header to all pages.
50db987 Include the first section in TOC.
555b62e Include the note about committing after staging the changes.
91f7d40 Explain various ways to stage changes.
edb3594 First draft of staging changes.
24e86ee Add command line and GUI tools to the objectives.
36cd6db Include the command prompt in code sample.
9b6ebfd Add a header to the page about initializing a repo.
fa1b75e Include the warning about removing .git directory.
dad47ed Write the first draft of initializing a repo.
fb0d184 Define the audience.
1ebb7a7 Define the objectives.
ca49180 Initial commit.
```

- `(HEAD -> master)` means `HEAD` is now at the tip of the master branch again.

---

## Summary

- Use `git log --oneline --all` at any point during `git bisect` to see exactly where `HEAD` is.
- `(HEAD)` in the log shows the current commit being tested during bisect.
- When you finish and reset, you're back on your branch tip.

---