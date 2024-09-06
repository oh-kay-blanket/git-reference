# Git ref

## GitHub

### Sub tree

For posting to gh-pages. Ensure that `dist/` directory is tracked first.  
`git subtree push --prefix dist origin gh-pages`

### Managing multiple accounts

* https://gist.github.com/rahularity/86da20fe3858e6b311de068201d279e3
* `git clone git@github.com-oh-kay-blanket:oh-kay-blanket/{the-repo-name}.git`
* Within repo `git config user.email "kayla.lee.plunkett@gmail.com"`

## Git

### Basic Workflow

`git init` creates a Git repository within the current directory  
`git init <project_name>` creates a Git repository in a new subdirectory

Basic components:

* Working Directory – where you actually make changes to files
* Staging Area – where you list what changes you’ve made
* Repository – holds the different versions of the project  

`git status` Inspects contents of the working directory and staging area  
`git add -A` adds files from the working directory to the staging area  
`git diff <file>` shows the difference between the working directory and the staging area  
`git commit -m 'Note changes here in quotes'` write in present tense. Permanently stores changes  
`git log` views history of commits

#### Add

`git add -A` stages everything in directory (and sub dirs)  
`git add .` stages new and modified (without deleted)  
`git add -u` adds modified and deleted (without new)

### Backtracking

#### Head commit

This is the commit you are currently on
`git show HEAD` Shows you the git log of the current commit

#### Checkout

`git checkout HEAD <file>` restores file in WD to last commit

#### Reset

`git reset HEAD <file>`resets the file in the staging area. Doesn’t discard WD changes, just removes changes from SA.  
`git reset <SHA>` Where SHA is the first 7 char of the previous commit you want to restore. This will set the SA back to that commit.

### Branching

So far we’ve only worked on the master branch. You can create other branches to test out different ideas.  
`git branch` Lists all branches and displays the active branch.  
`git branch <new_branch_name>` Creates a new branch  
`git checkout <branch_name>` Switches to that branch  
`git merge <branch_name>` Merges branch changes back to master branch

#### Merge conflict

If you had made changes to both master and another branch in the same spot and then tried to merge the two you would get a merge conflict. You must resolve the conflicts before you can merge the two.

#### Deleting a branch

It’s good to delete branches when you no longer need them.
git branch -d <branch_name> Deletes the branch

### Teamwork

#### Remotes

A shared git repository where multiple people can work on the same project and later merge changes.

`git clone <repository_directory> <clone_name>` creates a local copy of the repository for a person to work on.  
`git remote -v` Shows a list of remotes. Your own remote is referred to as origin

#### Fetch

`git fetch` Check to see if your remote is in sync with the main repo. It doesn’t merge into your local repo, it moves them to a remote branch.
`git merge origin/master` Merges the master branch into your local copy

#### Push

`git push origin <local_current_branch>:<new_branch_to_push_to>` Pushes your branch to the main repo where it can be reviewed and merged with the master.

### Workflow

Standard workflow includes:

1. Fetch and merge changes from the remote
2. Create a branch to work on a new project feature
3. Develop the feature on your branch and commit your work
4. Fetch and merge from the remote again (in case new commits were made while you were working)
5. Push your branch up to the remote for review
