# Git Commands Cheat Sheet (Days 22–25)

A comprehensive guide to version control workflows, from local configuration to advanced history manipulation.

---

## 1. Setup & Config
Establish your identity and configure your global Git environment.

```bash
# Set your global commit identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set the default branch name to main globally
git config --global init.defaultBranch main

# Check all active configurations and their origins
git config --list --show-origin
```

---

## 2. Basic Workflow
Track changes, stage assets, inspect modifications, and commit snapshots to your local timeline.

```bash
# Initialize a brand new local repository
git init

# View the status of your working directory (unstaged, staged, untracked files)
git status
# Short, compact status view
git status -s

# Stage changes for the next commit
git add file.txt       # Stage a specific file
git add .              # Stage all changes in the current directory

# Record staged snapshots to the history
git commit -m "Commit message"
git commit -am "Stage and commit modified tracked files in one step"

# Inspect changes between working directory, staging area, and commits
git diff               # Unstaged changes vs. last commit
git diff --staged      # Staged changes vs. last commit

# Explore commit history
git log                # Full history log
git log --oneline      # Compact, single-line history
git log --graph --oneline --all # Visual tree graph of all branches
```

---

## 3. Branching
Isolate lines of development to work on features or fixes safely.

```bash
# List branches
git branch             # List local branches
git branch -a          # List both local and remote-tracking branches

# Create branches
git branch feature-xyz # Create a new branch at current HEAD

# Navigate between branches
git checkout feature-xyz  # Switch using the classic command
git switch feature-xyz    # Switch using the modern, dedicated command
git switch -c new-feature # Create a new branch and immediately switch to it
```

---

## 4. Remote
Synchronize your local repository timeline with remote hosting servers (like GitHub or GitLab).

```bash
# Clone an existing remote repository locally
git clone <remote-url>

# Manage remote connections
git remote -v                          # View all connected remote aliases
git remote add origin <remote-url>     # Map a local repo to a new remote URL

# Fetch updates from the remote without merging them into your working files
git fetch origin

# Download remote updates and automatically merge them into your active branch
git pull origin main

# Upload local commits to the remote repository
git push origin main
git push -u origin feature-xyz         # Push and set the default upstream tracking branch
```
> *Note on Forking:* **Forking** is not a native Git command. It is a feature provided by hosting platforms (GitHub, GitLab) to duplicate an external repository directly onto your own remote account space. You then interact with it using native `clone`, `fetch`, and `push` commands.

---

## 5. Merging & Rebasing
Integrate histories and changes from one branch into another.

```bash
# ---- MERGING (Preserves historical context, creates a merge commit) ----
git switch main
git merge feature-xyz

# ---- REBASING (Rewrites history for a clean, linear timeline) ----
git switch feature-xyz
git rebase main
```

---

## 6. Stash & Cherry Pick
Save incomplete work temporarily or surgically pluck individual commits across branches.

```bash
# ---- STASHING (Shelve dirty working directory changes safely) ----
git stash              # Save tracked modifications to a temporary stack
git stash list         # View all saved items in the stash stack
git stash pop          # Apply the latest stashed changes and remove them from the stack
git stash apply        # Apply the latest stashed changes but keep them in the stack

# ---- CHERRY PICKING (Apply a specific commit from anywhere to your current HEAD) ----
git cherry-pick <commit-hash>
```

---

## 7. Reset & Revert
Undo mistakes, modify staging logs, or gracefully rewrite state tracking.

```bash
# ---- REVERTING (Safe for shared/public branches; creates a new "anti-commit") ----
git revert <commit-hash>

# ---- RESETTING (Dangerous; rewrites history; use for local cleanup only) ----
git reset --soft HEAD~1  # Undo commit; keep changes staged in your index
git reset --mixed HEAD~1 # Undo commit and unstage changes; keep files in working directory (Default)
git reset --hard HEAD~1  # Undo commit, unstage changes, and DESTROY all uncommitted local modifications
```
