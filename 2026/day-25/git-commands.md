# Git Commands Cheat Sheet (Days 22–25)

A practical guide to Git version control and GitHub CLI (`gh`) workflows, from local configuration to repository management and CI/CD inspection.

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

Track changes, stage files, inspect modifications, and commit snapshots.

```bash
# Initialize a new local repository
git init

# Inspect working-tree status
git status
git status -s                    # Short status view

# Stage changes
git add file.txt                 # Stage one file
git add .                        # Stage changes under the current directory

# Commit staged changes
git commit -m "Commit message"

# Commit modifications to tracked files (does not include new untracked files)
git commit -am "Update tracked files"

# Compare changes
git diff                         # Unstaged changes
git diff --staged                # Staged changes

# Inspect history
git log
git log --oneline
git log --graph --oneline --all  # Visual graph of all branches
```

---

## 3. Branching

Use branches to isolate features, fixes, and experiments.

```bash
# List branches
git branch                       # Local branches
git branch -a                    # Local and remote-tracking branches

# Create a branch
git branch feature-xyz

# Switch branches
git checkout feature-xyz         # Classic command
git switch feature-xyz            # Modern command
git switch -c new-feature         # Create and switch
```

---

## 4. Remote Repositories

Synchronize local work with a remote host such as GitHub or GitLab.

```bash
# Clone an existing repository
git clone <remote-url>

# Inspect and configure remotes
git remote -v
git remote add origin <remote-url>

# Synchronize changes
git fetch origin                 # Download remote refs without merging
git pull origin main             # Fetch and integrate main
git push origin main             # Push local main
git push -u origin feature-xyz   # Push and set upstream tracking
```

**Forking note:** Forking is a hosting-platform feature, not a native Git command. A fork creates a copy of a repository under another account or organization.

---

## 5. Merging & Rebasing

Integrate work from one branch into another.

```bash
# Merge a feature branch into main
git switch main
git merge feature-xyz

# Rebase a feature branch onto main
git switch feature-xyz
git rebase main
```

Merging preserves branch history and may create a merge commit. Rebasing replays commits onto a new base and rewrites commit IDs; avoid rebasing shared branches unless the team agrees.

---

## 6. Stash & Cherry-Pick

Temporarily save local changes or apply a specific commit to the current branch.

```bash
git stash                         # Save tracked changes
git stash list                    # List stashes
git stash pop                     # Apply latest stash and remove it
git stash apply                   # Apply latest stash but keep it

git cherry-pick <commit-hash>     # Apply one commit to current branch
```

---

## 7. Reset & Revert

Undo changes carefully.

```bash
# Revert: create a new commit that reverses an earlier commit
git revert <commit-hash>

# Reset: move the current branch pointer
git reset --soft HEAD~1           # Keep changes staged
git reset --mixed HEAD~1          # Keep changes unstaged (default)
git reset --hard HEAD~1           # Discard changes; destructive
```

Use `git revert` for commits already shared with others. `git reset --hard` can permanently discard uncommitted work, so check `git status` first.

---

## 8. GitHub CLI (`gh`) Setup

GitHub CLI lets you manage repositories, issues, pull requests, releases, and Actions workflows from a terminal.

```bash
# Check that GitHub CLI is installed
gh --version

# Sign in to GitHub
gh auth login

# Check current authentication status
gh auth status

# Refresh authentication to add the permission needed to delete repositories
gh auth refresh -h github.com -s delete_repo
```

Only request extra scopes when you need them. The `delete_repo` scope is powerful and should be granted only when required.

---

## 9. GitHub Repository Management

```bash
# Clone a repository (owner/repository is explicit and unambiguous)
gh repo clone Yogesh3052/github_cli

# Create a repository interactively
gh repo create

# Create a private repository with a specific name
gh repo create github_cli --private

# View repository details
gh repo view Yogesh3052/github_cli

# List repositories for the authenticated user
gh repo list

# Delete a repository (DESTRUCTIVE; double-check the target)
gh repo delete Yogesh3052/github_cli
```

If you are already inside the repository, commands such as `gh repo view` can usually infer the current repository. Use `OWNER/REPO` when working from another directory or when you want to be explicit.

---

## 10. GitHub Issues

```bash
# Create an issue in a repository (interactive prompts)
gh issue create --repo Yogesh3052/github_cli

# List issues
gh issue list --repo Yogesh3052/github_cli

# View issue number 1
gh issue view 1 --repo Yogesh3052/github_cli

# Close issue number 1
gh issue close 1 --repo Yogesh3052/github_cli
```

Issue numbers are repository-specific. Replace `1` with an issue number that actually exists.

---

## 11. Pull Requests & GitHub Actions

```bash
# List pull requests for the current repository
gh pr list

# List workflow runs for a repository
gh run list --repo Yogesh3052/Application-to-CICD

# View details for a specific workflow run
gh run view 34041560822 --repo Yogesh3052/Application-to-CICD

# View logs for a failed run
gh run view 34041560822 --repo Yogesh3052/Application-to-CICD --log-failed
```

Use `gh run list` to find recent runs, then copy a run ID into `gh run view`. The run ID above is an example from the command list and may no longer exist or may not be accessible to your account.

---

## 12. More Useful GitHub CLI Commands to Explore

### `gh api` — Call the GitHub REST API

Useful for checking details or automating tasks not covered by a dedicated `gh` command.

```bash
# Get the authenticated user's profile
gh api user

# List repositories for an owner
gh api users/Yogesh3052/repos --paginate

# Get details for a repository
gh api repos/Yogesh3052/github_cli
```

### `gh gist` — Create and Manage Gists

Gists are useful for sharing snippets, small scripts, and notes.

```bash
# Create a public gist from a local file
gh gist create script.sh

# Create a private/unlisted gist from a file
gh gist create script.sh --private

# List your gists
gh gist list

# View a gist
gh gist view <gist-id>
```

Review a file before publishing it; never put credentials, tokens, or other secrets in a gist.

### `gh release` — Manage Releases

Releases attach versioned notes and assets to repository tags.

```bash
# List releases
gh release list --repo OWNER/REPO

# View a release
gh release view v1.0.0 --repo OWNER/REPO

# Create a release from an existing tag
gh release create v1.0.0 --repo OWNER/REPO --generate-notes

# Upload a build artifact to a release
gh release upload v1.0.0 ./dist.zip --repo OWNER/REPO
```

Replace `OWNER/REPO`, tag names, and file paths with your actual values. A release command may publish content to a public audience depending on repository visibility.

### `gh alias` — Create Shortcuts

Aliases reduce typing for commands you run often.

```bash
# Create a shortcut to list pull requests
gh alias set prs 'pr list'

# Run the shortcut
gh prs

# List configured aliases
gh alias list

# Remove an alias
gh alias delete prs
```

### `gh search repos` — Search GitHub Repositories

Search repositories directly from the terminal.

```bash
# Search repositories by topic/keyword
gh search repos "kubernetes platform engineering"

# Limit the number of results
gh search repos "devops" --limit 10

# Search by language
gh search repos "cloud automation" --language=Python --limit 10
```

---

## 13. Quick Practice Checklist

- [ ] Run `gh auth status` and confirm you are signed in.
- [ ] Clone a repository you have permission to access.
- [ ] View and list repositories with `gh repo view` and `gh repo list`.
- [ ] Create a test issue, list it, view it, and close it.
- [ ] Inspect a GitHub Actions run with `gh run list` and `gh run view`.
- [ ] Try read-only API requests with `gh api user` and `gh api repos/OWNER/REPO`.
- [ ] Create a gist only from a safe, non-sensitive test file.
- [ ] Explore releases on a test repository before creating one.
- [ ] Create and use an alias such as `gh prs`.
- [ ] Search for repositories using `gh search repos`.

**Safety reminder:** Prefer read-only commands while learning. Repository deletion, release publication, issue closure, and publishing gists can have lasting effects. Check the target and visibility before confirming.
