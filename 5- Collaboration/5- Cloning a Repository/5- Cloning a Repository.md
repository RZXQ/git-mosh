# Checking Remote Repositories in Git

When you clone a repository, you can check which remote repositories are connected using:

```
bash git remote
``` 

or for detailed URLs:

```
bash git remote -v
``` 

This displays the remote name (typically `origin`) and its fetch/push URLs.

**Example Output:**

```
origin [https://github.com/codewithmosh/Mars.git](https://github.com/codewithmosh/Mars.git) (fetch) origin [https://github.com/codewithmosh/Mars.git](https://github.com/codewithmosh/Mars.git) (push)
``` 

**Tip:**

- `origin` is just a local alias for the actual repository URL.
- You can add, rename, or remove remotes as needed for collaboration or deployment.
```