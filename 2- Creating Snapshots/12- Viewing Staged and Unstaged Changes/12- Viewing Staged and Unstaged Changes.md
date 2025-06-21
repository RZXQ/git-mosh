## The Two Main Git Diff Commands

### 1. `git diff` - Shows Unstaged Changes

``` bash
git diff
```

**What it shows**: Changes you made but haven't staged yet

- Compares: Your current files vs what's in the staging area
- Think of it as: "What changes am I about to stage?"

### 2. - Shows Staged Changes `git diff --staged`

``` bash
git diff --staged
# OR (same thing)
git diff --cached
```

**What it shows**: Changes you've staged but haven't committed yet

- Compares: What's in staging area vs your last commit
- Think of it as: "What changes am I about to commit?"

## Simple Example to Understand

Let's say you have a file called `hello.txt`:

### Step 1: Make changes and check unstaged diff

``` bash
echo "Hello World" > hello.txt    # Create/modify file
git diff                          # Shows your new changes
```

This shows what you changed but haven't staged yet.

### Step 2: Stage the changes and check staged diff

``` bash
git add hello.txt                 # Stage the changes
git diff --staged                 # Shows what's ready to commit
```

This shows what you're about to commit.

### Step 3: Make more changes and see both diffs

``` bash
echo "Goodbye" >> hello.txt       # Add more content
git diff                          # Shows newest unstaged changes
git diff --staged                 # Shows previously staged changes
```

## Quick Memory Tips

- **`git diff`** = "What changes haven't I staged yet?"
- **`git diff --staged`** = "What changes am I about to commit?"

## About vs `--cached``--staged`

Both and do exactly the same thing. Use because it's clearer and matches Git's terminology.
`git diff --cached``git diff --staged``--staged`

## The Big Picture

Think of Git as having three places for your files:

1. **Working Directory** (your current files)
2. **Staging Area** (changes ready to commit)
3. **Repository** (committed changes)

- `git diff` shows: Working Directory vs Staging Area
- shows: Staging Area vs Repository `git diff --staged`
