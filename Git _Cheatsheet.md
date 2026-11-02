# Git Cheatsheet

## 1. Git Basics

| Command | Description |
|---|---|
| `git --version` | Check Git version |
| `git config --list` | View Git configuration |
| `git status` | Check repository status |
| `git help` | Display Git help |
| `git help commit` | Get help for a specific command |

## 2. Git Configuration

Set your username and email before making commits.

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

| Command | Description |
|---|---|
| `git config user.name` | Check username |
| `git config user.email` | Check email |
| `git config --global --list` | View global configuration |
| `git config --global --unset user.name` | Remove configured username |

## 3. Repository Setup

| Command | Description |
|---|---|
| `git init` | Initialize a new Git repository |
| `git clone <url>` | Clone an existing repository |
| `git status` | Check repository status |
| `git rev-parse --show-toplevel` | Show repository root directory |

Example:

```bash
git init
```

Clone a repository:

```bash
git clone https://github.com/username/project.git
```

## 4. Staging and Committing

| Command | Description |
|---|---|
| `git add file.py` | Stage a specific file |
| `git add .` | Stage changes in the current directory |
| `git add -A` | Stage all changes in the repository |
| `git status` | Check staged and unstaged changes |
| `git commit -m "message"` | Commit staged changes |
| `git commit -am "message"` | Stage and commit tracked-file modifications |
| `git diff` | View unstaged changes |
| `git diff --staged` | View staged changes |

Example workflow:

```bash
git add .
git commit -m "Added Python programs"
```

## 5. Git Log and History

| Command | Description |
|---|---|
| `git log` | Display commit history |
| `git log --oneline` | Display compact commit history |
| `git log --oneline --all` | Show commits from all branches |
| `git log -5` | Display the latest five commits |
| `git show` | Display details of the latest commit |
| `git show <commit_id>` | Display a specific commit |

## 6. Branching

Branches allow you to work on different features independently.

| Command | Description |
|---|---|
| `git branch` | List local branches |
| `git branch -a` | List all local and remote branches |
| `git branch branch_name` | Create a new branch |
| `git switch branch_name` | Switch to another branch |
| `git switch -c branch_name` | Create and switch to a new branch |
| `git branch -d branch_name` | Delete a merged branch |
| `git branch -D branch_name` | Force-delete a branch |
| `git branch -m new_name` | Rename the current branch |

Example:

```bash
git switch -c feature-login
```

## 7. Merging Branches

Merging combines changes from one branch into another.

```bash
git switch main
git merge feature-login
```

| Command | Description |
|---|---|
| `git merge branch_name` | Merge another branch into the current branch |
| `git merge --abort` | Abort a merge in progress |
| `git merge --continue` | Continue a merge after resolving conflicts |

### Merge Conflicts

A merge conflict happens when Git cannot automatically combine changes.

Steps to resolve:

1. Open the conflicted file.
2. Find the conflict markers.
3. Decide which changes to keep.
4. Remove the conflict markers.
5. Stage the resolved file.
6. Complete the merge commit if required.

```bash
git add .
git commit
```

## 8. Remote Repository

A remote repository is a version of your project hosted on platforms such as GitHub or GitLab.

| Command | Description |
|---|---|
| `git remote` | List remote names |
| `git remote -v` | Display remote URLs |
| `git remote add origin <url>` | Add a remote repository |
| `git remote remove origin` | Remove a remote |
| `git remote rename old new` | Rename a remote |
| `git remote set-url origin <url>` | Change remote URL |

Example:

```bash
git remote add origin https://github.com/username/project.git
```

## 9. Push and Pull

| Command | Description |
|---|---|
| `git push` | Push commits to the remote branch |
| `git push origin main` | Push the main branch |
| `git push -u origin main` | Push and set upstream tracking |
| `git pull` | Fetch and integrate remote changes |
| `git pull origin main` | Pull changes from the remote main branch |
| `git fetch` | Download remote updates without integrating them |
| `git fetch --all` | Fetch updates from all remotes |

### Difference Between Fetch and Pull

- `git fetch`: Downloads remote changes but does not merge them into your current branch.
- `git pull`: Fetches remote changes and integrates them into your current branch.

## 10. Git Stash

Stash temporarily saves changes without creating a commit.

| Command | Description |
|---|---|
| `git stash` | Temporarily save tracked-file changes |
| `git stash push -m "message"` | Save changes with a description |
| `git stash list` | Display saved stashes |
| `git stash pop` | Apply the latest stash and remove it |
| `git stash apply` | Apply the latest stash without removing it |
| `git stash drop` | Delete the latest stash |
| `git stash clear` | Delete all stashes |

Example:

```bash
git stash
git switch main
git stash pop
```

## 11. Undo Changes

| Command | Description |
|---|---|
| `git restore file.py` | Discard unstaged changes in a file |
| `git restore .` | Discard all unstaged changes in the current directory |
| `git restore --staged file.py` | Remove a file from staging |
| `git reset --soft HEAD~1` | Undo the latest commit but keep changes staged |
| `git reset --mixed HEAD~1` | Undo the latest commit and unstage changes |
| `git reset --hard HEAD~1` | Remove the latest commit and its changes |
| `git revert <commit_id>` | Create a new commit that reverses an earlier commit |

**Important:** `git reset --hard` can permanently discard uncommitted changes. Use it carefully.

## 12. .gitignore

`.gitignore` tells Git which files and directories should not be tracked.

Example `.gitignore`:

```gitignore
# Python cache
__pycache__/
*.pyc

# Virtual environment
.venv/
venv/

# Environment variables
.env

# IDE settings
.vscode/

# System files
.DS_Store
```

Common commands:

```bash
touch .gitignore
git status
```




