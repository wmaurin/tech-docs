# Git Command Reference

## Configuration

```bash
# Set user name and email
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# List all configuration
git config --list

# Set default branch name
git config --global init.defaultBranch main
```

## Repository Setup

```bash
# Initialize a new repository
git init

# Clone a repository
git clone <url>
git clone <url> <directory>

# Clone specific branch
git clone -b <branch> <url>
```

## Basic Workflow

```bash
# Check status
git status

# Add files to staging
git add <file>
git add .                    # Add all changes
git add -p                   # Interactive staging

# Commit changes
git commit -m "message"
git commit -am "message"     # Add tracked files and commit

# View commit history
git log
git log --oneline
git log --graph --oneline --all
```

## Branching

```bash
# List branches
git branch                   # Local branches
git branch -a                # All branches (including remote)

# Create and switch branches
git branch <name>            # Create branch
git checkout <name>          # Switch branch
git checkout -b <name>       # Create and switch
git switch <name>            # Switch (newer syntax)
git switch -c <name>         # Create and switch (newer syntax)

# Delete branches
git branch -d <name>         # Delete (safe)
git branch -D <name>         # Force delete
```

## Merging & Rebasing

```bash
# Merge branch into current
git merge <branch>

# Rebase current branch
git rebase <branch>
git rebase -i HEAD~3         # Interactive rebase last 3 commits

# Abort operations
git merge --abort
git rebase --abort
```

## Remote Operations

```bash
# List remotes
git remote -v

# Add remote
git remote add origin <url>

# Fetch and pull
git fetch
git pull
git pull --rebase

# Push changes
git push
git push -u origin <branch>  # Set upstream
git push --force-with-lease  # Safe force push
```

## Stashing

```bash
# Stash changes
git stash
git stash -m "message"

# List stashes
git stash list

# Apply stash
git stash pop                # Apply and remove
git stash apply              # Apply and keep

# Drop stash
git stash drop
```

## Undoing Changes

```bash
# Discard working directory changes
git checkout -- <file>
git restore <file>           # Newer syntax

# Unstage files
git reset HEAD <file>
git restore --staged <file>  # Newer syntax

# Reset commits
git reset --soft HEAD~1      # Keep changes staged
git reset --mixed HEAD~1     # Keep changes unstaged
git reset --hard HEAD~1      # Discard changes

# Revert a commit (creates new commit)
git revert <commit>
```

## Inspection

```bash
# Show changes
git diff                     # Working directory vs staging
git diff --staged            # Staging vs last commit
git diff <branch1> <branch2>

# Show commit details
git show <commit>

# Blame (who changed what)
git blame <file>
```

## Tags

```bash
# List tags
git tag

# Create tags
git tag <name>               # Lightweight tag
git tag -a <name> -m "msg"   # Annotated tag

# Push tags
git push origin <tag>
git push --tags              # Push all tags
```

