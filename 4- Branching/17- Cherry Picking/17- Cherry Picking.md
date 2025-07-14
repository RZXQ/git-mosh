# Git Cherry-Pick Conflict Resolution Short Guide

1. Start the cherry-pick:
   ```bash
   git cherry-pick <commit-sha>
   ```

2. If there’s a conflict, edit the affected file(s) to resolve the conflict:
   ```bash
   vi toc.txt
   # Edit to resolve
   ```

3. Mark resolved files as staged:
   ```bash
   git add toc.txt
   ```

4. Continue applying the cherry-picked commit:
   ```bash
   git cherry-pick --continue
   ```

# Notes

- Don’t use `git commit` directly while resolving a cherry-pick conflict; always use `git cherry-pick --continue`.
- Use `git status` anytime to check what’s left to do.