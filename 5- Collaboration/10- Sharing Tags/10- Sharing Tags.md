## Pushing and Deleting Tags with Git

By default, **`git push`** only sends branch updates to the remote—it does **not** send your local tags automatically.
If you want to publish a **tag** to your remote repository, you need to push it explicitly.

### **Push a Tag to the Remote**

``` bash
git push origin v1.0
```

- **Purpose:**
  Uploads the tag from your local repository to the remote named `origin`. `v1.0`
-

The remote repo will now have the tag, making it accessible to others. **Effect:**`v1.0`

### **Delete a Tag from the Remote**

``` bash
git push origin --delete v1.0
```

- **Purpose:**
  Removes the tag named from the remote repository. `v1.0`
-

Anyone pulling from the remote will no longer see this tag (unless it exists locally). **Effect:**

### **Summary Table**

| Command                       | Action                                 |
|-------------------------------|----------------------------------------|
| git push origin v1.0          | Push tag to remote `origin` `v1.0`     |
| git push origin --delete v1.0 | Delete tag from remote `origin` `v1.0` |

If you ever want to push all your local tags at once, you can use: **Tip:**

``` bash
git push --tags
```
