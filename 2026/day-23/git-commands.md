#Git commands
## Git commands for Setup & Config
-git init
    What is does:- initialize the git repository
    how to use:- open the folder for which you want to initialze git repo
    and enter git "init command".
-git config --global user.email <"your email id">
    what is does:- Configures the user email for git repo. Email is used to authenticate the user while making the commit.
    how to use:- git config --global user.email "yogesh@gmail.com"
-git config --global user.name <"username">
    what it does :- Configures the username for the git repo. Username is used to authenticate the user while making the commit.
    how to use:- git config --global user.name "yogesh"

##GIT Workflow commands
-git add . or git add <filename>
    What is does:- this command adds the untracked file into the staging area. "." is used when you have to add all the files. You cannot add directly commit untracked files without adding it to staging area.
    how to use:- git add . || git add file.txt
-git diff
    What is does:- Using this commands we can compare states in git repo. for eg- we can compare commit1 and commit2.
    how to use:- git diff || git diff commit1 commit2 || git diff branch1 branch2
-git commit
    What it does:- this commad commit the changes to git repo.
    how to use:- git commit -m "this is my first commit"

##Git commands for viewing changes
-git status
    what it does:- it shows which files are untracked, staging area and tracked files.
    how to use:- git status
## GIt Branching commands
-git branch
    what it does:- it lists out all the branches in the git repo
    how to use:- git branch
-git checkout -b featue-1
    what it does:-It creates a new branch and switches into it.
    how to use:- git checkout -b < branch name>
-git switch -c feature-2
    what it does:- it also creates a new branch and switches into it.
    how to use:- git switch -c < branch name>
-git switch feature2
    what it does:- it only switches to the another branch
    how to use: git switch < branch name>
-git checkout feature-2
    what it does:- it only switches to another branch
    how to use:-git checkout < branch name>