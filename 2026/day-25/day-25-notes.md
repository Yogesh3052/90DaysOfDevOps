## What is the difference between --soft, --mixed, and --hard?
### ANS:- In --soft, the commit is deleted till target, but the file is still present in stage. --mixed is the by default in git reset. IT also deletes the commit till the target and also delete the file from stage but the file is present in working directory. In --hard the commit is erased from  histroy, stage, and working directory.

## Which one is destructive and why?
### ANS:- --hard is more destructive as it erases the file completly and cannot be recovered. Therefore if the file is important --hard should not be used.

## When would you use each one?
### ANS:- you should use --soft if you want to undo commit but you also want changes to be staged. you should use --mixed is you want to undo commit and unstage changes but the changes should be safe in working directory. you should use --hard if you are ok if the changes and commit is completely erased.

## Should you ever use git reset on commits that are already pushed?
### ANS:- you should avoid using git reset on shared repo. As git reset changes the commit history and if other user pulles those then this can change their local repo and there can also be chances of merge confict.

## How is git revert different from git reset?
### ANS:- to undo previous changes git revert create commit which undo changes in previous changes. It does not changes the commit history.

## Why is revert considered safer than reset for shared branches?
### ANS:- to undo previous changes git revert create commit which undo changes in previous changes. It does not changes the commit history. whereas git reset changes the commit history while undo changes. when commit history changes there are chances of merge conflicts and also unwanted code to merge.

## When would you use revert vs reset?
### when you are working with public or shared repos you should use git revert. If you are working on private or local repos it is safe to use git reset.

| | `git reset` | `git revert` |
|---|---|---|
| What it does | undos changes by delelting commit from commit history | undos change by creating opposite commit |
| Removes commit from history? | yes | no |
| Safe for shared/pushed branches? | no | yes |
| When to use | for local/ private repos | for shared/ pushed branches |