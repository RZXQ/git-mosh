## Starting Point

We have an existing file: file1.js (already tracked by Git)

## Step 1: Making changes to files

``` bash
echo sky >> file1.js    # Add "sky" to the end of existing file1.js
echo sky >> file2.js    # Create new file2.js and add "sky" to it
```

## Step 2: Check what Git sees

``` bash
git status -s
```

**Understanding the columns:**

- **Left column**: Shows status in the staging area (what will be committed)
- **Right column**: Shows status in the working directory (current changes)

## Step 3: Add file1.js to staging area

``` bash
git add file1.js    
git status -s
M  file1.js     # M in left column = Modified and staged (ready to commit)
?? file2.js     # ?? = Untracked file (Git doesn't know about it yet)
```

## Step 4: Make more changes to file1.js

``` bash
echo ocean >> file1.js    # Add "ocean" to file1.js (now it has both "sky" and "ocean")
git status -s
MM file1.js     # First M = staged changes, Second M = unstaged changes
?? file2.js     # Still untracked
```

**Explanation**: file1.js now has TWO different states:

- Staged version: has "sky" added (ready to commit)
- Working version: has both "sky" AND "ocean" (newer changes not staged yet)

## Step 5: Stage the newer changes

``` bash
git add file1.js    # Stage the latest version (with both "sky" and "ocean")
git status -s
M  file1.js     # Only left M = all changes are now staged
?? file2.js     # Still untracked
```

## Step 6: Add the new file to staging

``` bash
git add file2.js
git status -s
M  file1.js     # M in left = Modified existing file, staged
A  file2.js     # A in left = Added new file, staged
```

## Quick Reference - Status Symbols:

- `M[space]` = Modified file, changes staged
- `[space]M` = Modified file, changes not staged
- `MM` = Modified file with both staged and unstaged changes
- `A[space]` = New file added to staging area
- `??` = Untracked file (Git doesn't know about it)
- `D[space]` = Deleted file, deletion staged
- `[space]D` = Deleted file, deletion not staged

## Key Concepts:

1. **Staging Area**: Like a preparation area where you collect changes before committing
2. **Working Directory**: Your current files with all your latest changes
3. : Left = staged (ready to commit), Right = working directory changes **Two-column system**

## Remember:

Git tracks files in different "zones":

- **Working Directory**: Where you make changes
- **Staging Area**: Where you prepare changes for commit
- **Repository**: Where committed changes are permanently stored
