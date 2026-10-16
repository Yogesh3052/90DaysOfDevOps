## What is a fast-forward merge?
### ANS:- Fast forward merge simply move commit forward. it simply move the main branch pointer to feature branch

## When does Git create a merge commit instead?
### ANS :- when there are diversifying changes git creates merge commit.

## What is a merge conflict?
### ANS:- it is the event when git is unable to combine changes of two branches. It occurs when there differce in the same line and in same file.

## What does rebase actually do to your commits?
### ANS:- It rearranges the commit history.

## How is the history different from a merge?
### ANS:- merge write the history in the chronological order and git rebase rewrite the git history in the clean format.

## Why should you never rebase commits that have been pushed and shared with others?
### ANS:- rebasing commit changes cyrptographic SHA hashes. when some one pulls the commit before rebase it breaks the syncronization between the repos.

## When would you use rebase vs merge?
### ANS:- when you want to clean commit history or private/ local repo you should use rebase. when you want accurate commit history or you are working on public/ shared repo you should use merge.

## What does squash merging do?
### ANS:- squash merge compress all the individual commits in single commit and the it append it into the main branch.

## When would you use squash merge vs regular merge?
### when you priortise complete granular level traceblity you do regular merge but when you want high level project timeline you squash merge.


## What is the difference between git stash pop and git stash apply?
### ANS:- git stash pop only stashs back the changes into the working directory but git stash apply stash back the changes back into the working directory as well as saves it into the stash list.

## When would you use stash in a real-world workflow?
### ANS:- when you have tracked files or uncommited changes but you want to change the branch to fix some bug you first stash the changes and then you switch the branch.

## What does cherry-pick do?
### ANS:-git cherry-pick allows you to select one specific commit from any branch and apply it as a brand new commit onto your current active branch.

## When would you use cherry-pick in a real project?
### ANS:- I would use cherry pick  if a critical bug is fixed on our active develop branch, but that branch contains 10 other half-finished features that aren't ready for deployment, we cannot merge the entire branch.
### Instead, I would checkout the main (production) branch and cherry-pick just that single bug-fix commit directly into production, leaving the unready features behind

## What can go wrong with cherry-picking?
### When you cherry-pick, Git copies the code changes but creates a brand-new commit ID. Because the IDs are different, Git thinks they are completely unrelated changes. Later, when you try to merge the two branches, Git gets confused seeing two different commits modifying the exact same lines of code, resulting in an artificial merge conflict you have to fix by hand.