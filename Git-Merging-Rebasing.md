# Git Merging and Rebasing

## Git Merge

Git merge is used to combine changes from one branch into another.

### Syntax

```bash
git merge <branch-name>
```

### Example

```bash
git checkout main
git merge feature
```

This merges the `feature` branch into the `main` branch.

---

## Fast-Forward Merge

A fast-forward merge occurs when the target branch has not diverged from the source branch.

### Example

```text
A --- B --- C (main)
             \
              D --- E (feature)
```

After merging:

```text
A --- B --- C --- D --- E (main)
```

Git simply moves the branch pointer forward without creating a merge commit.

### Command

```bash
git merge feature
```

---

## Merge Conflicts

A merge conflict occurs when Git cannot automatically determine which changes to keep.

### Example

Two developers modify the same line in a file:

```text
Developer A: Hello Git
Developer B: Hello GitHub
```

When merging, Git reports a conflict.

### Check Conflicts

```bash
git status
```

### Resolve Conflict

1. Open the conflicted file.
2. Edit the file manually.
3. Save the file.
4. Stage the file.

```bash
git add file.txt
```

5. Complete the merge.

```bash
git commit
```

---

## Git Rebase

Rebase moves or reapplies commits from one branch onto another branch.

### Syntax

```bash
git rebase <branch-name>
```

### Example

```bash
git checkout feature
git rebase main
```

This places feature branch commits on top of the latest main branch commits.

### Before Rebase

```text
A --- B --- C (main)
       \
        D --- E (feature)
```

### After Rebase

```text
A --- B --- C --- D' --- E' (feature)
```

The commit history becomes linear and cleaner.

---

## Rebase Conflict Resolution

If conflicts occur during rebase:

```bash
git status
```

Resolve the conflict and continue:

```bash
git add .
git rebase --continue
```

To abort the rebase:

```bash
git rebase --abort
```

---

## Difference Between Merge and Rebase

| Feature        | Merge                         | Rebase                          |
| -------------- | ----------------------------- | ------------------------------- |
| History        | Preserves complete history    | Creates linear history          |
| Merge Commit   | Creates a merge commit        | No merge commit                 |
| Complexity     | Easier and safer              | More powerful but riskier       |
| Collaboration  | Preferred for shared branches | Best for local/private branches |
| Commit History | Non-linear                    | Clean and linear                |

### Merge Example

```text
A --- B --- C
      \     \
       D --- E
```

### Rebase Example

```text
A --- B --- C --- D' --- E'
```

---

## Best Practices

* Use **merge** for shared branches.
* Use **rebase** to clean up local commit history.
* Avoid rebasing public branches that others are using.
* Resolve conflicts carefully before continuing.

## Useful Commands

```bash
git merge feature
git merge --abort

git rebase main
git rebase --continue
git rebase --abort

git log --oneline --graph --all
```

## Summary

* `git merge` combines branches and preserves history.
* Fast-forward merge occurs when no divergent commits exist.
* Merge conflicts happen when Git cannot automatically combine changes.
* `git rebase` creates a cleaner, linear history.
* Use merge for collaboration and rebase for maintaining clean local commits.
