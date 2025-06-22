## Basic Log Commands

### View All Commits

``` bash
git log --oneline
```

**What it does:** Lists all the previous changes made in your project, showing each commit on a single line with a short
hash and commit message.
**When to use:** When you want to see the entire history of your project in a compact format.

### View Recent Commits

``` bash
git log --oneline -3
```

**What it does:** Lists just the most recent 3 changes made in your project.
**When to use:** When you only care about the latest few commits and don't want to scroll through the entire history.

## Filtering by Author

### View Commits by Specific Person

``` bash
git log --oneline --author="Mosh"
```

**What it does:** Shows all changes made by a specific person named "Mosh."
**When to use:** When you want to see what contributions a particular team member has made to the project.

## Filtering by Date

### View Commits Before a Date

``` bash
git log --oneline --before="2020-08-17"
```

**What it does:** Shows all changes made before August 17, 2020.
**When to use:** When you need to see the state of the project up to a certain point in time.

### View Commits After a Date

``` bash
git log --oneline --after="2020-08-17"
```

**What it does:** Shows all changes made after August 17, 2020.
**When to use:** When you want to see recent changes since a specific date.

### View Recent Commits (Relative Dates)

``` bash
git log --oneline --after="yesterday"
```

**What it does:** Shows all changes made since yesterday.
**When to use:** For daily standup meetings or quick recent activity checks.

``` bash
git log --oneline --after="one week ago"
```

**What it does:** Shows all changes made in the last week.
**When to use:** For weekly progress reviews or sprint retrospectives.

## Searching Commits

### Search Commit Messages

``` bash
git log --oneline --grep="GUI"
```

**What it does:** Shows all changes where the commit message includes the word "GUI".
**When to use:** When you want to find commits related to a specific feature or topic mentioned in commit messages.

### Search Code Changes (String Search)

``` bash
git log --oneline -S"hello()"
```

**What it does:** Shows changes where the text was added or removed in the actual code files. `hello()`
**Note:** The stands for "String" and searches for additions/deletions of specific text in the code. `-S`
**When to use:** When you want to track when a specific function, variable, or piece of code was introduced or removed.

``` bash
git log --oneline -S"OBJECTIVES"
```

**What it does:** Shows changes where the word `OBJECTIVES` was added or removed in the code.

### Search with Detailed Changes

``` bash
git log --oneline -S"OBJECTIVES" --patch
```

**What it does:** Shows changes with `OBJECTIVES` added or removed, and also displays exactly what was changed in the
code (the actual diff).
**When to use:** When you not only want to find when something changed, but also see the specific lines that were
modified.

## Range-Based Queries

### View Commits Between Two Points

``` bash
git log --oneline fb0d184..edb3594
```

**What it does:** Shows changes between two specific points in history (from commit `fb0d184` up to commit `edb3594`).
**When to use:** When you want to see what changed between two releases, branches, or specific commits.

## File-Specific Queries

### View Changes to Specific File

``` bash
git log --oneline toc.txt
```

**What it does:** Shows all changes that involved the file called . `toc.txt`
**When to use:** When you want to see the history of modifications to a particular file.

``` bash
git log --oneline -- toc.txt
```

**What it does:** Another way to show all changes that involved (the `--` is used to separate options from file paths).
`toc.txt`
**When to use:** Same as above, but more explicit syntax that's useful when file names might be confused with branch
names.

### View File Changes with Details

``` bash
git log --oneline --patch -- toc.txt
```

**What it does:** Shows all changes that involved along with the actual code differences (what lines were added,
removed, or modified). `toc.txt`
**When to use:** When you want to see not just when a file was changed, but exactly what those changes were.

## Quick Reference Summary

| Command Pattern   | Purpose                       |
|-------------------|-------------------------------|
| `--oneline`       | Compact, one-line format      |
| `-3`              | Limit to recent N commits     |
| `--author="name"` | Filter by person              |
| `--before="date"` | Show commits before date      |
| `--after="date"`  | Show commits after date       |
| `--grep="text"`   | Search commit messages        |
| `-S"text"`        | Search code changes           |
| `--patch`         | Show actual code differences  |
| `hash1..hash2`    | Show range between commits    |
| `filename`        | Show changes to specific file |
