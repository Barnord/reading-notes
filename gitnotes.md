CVCS, or Centralized Version Control System, these systems have a single server that logs all changes and versions of uploaded files. GitHub is a DVCS, which is similar, except clients can clone repositories, which can be placed back on the server in the event any data is lost, which addresses the failure point of the CVCS. Git stores snapshots, every time you save, or commit files, Git saves the save with a reference. In the event of data loss, or corruption, you can access your old saves through Git. Through committing individual files, Git allows for non-linear development via many branches.


### Importing
- git init
- git add*.c
- git add license
- git commit -m "commit notes go here"
I don't understand any of this yet

### Cloning
-git clone (address from the button on the git site) (name of directory you want it in, defaults to repository name if empty) = this copies all versions of all the files for the cloned project. Also retrieves a copy of the newest version of the project.


## Workflow

### Local Repository Structure
A local Git repo has 3 components
1. Working Directory
2. Index
3. Head

### Saving Changes
Everything in the working directory is iehter tracked or untracked, tracked files were part of the most recent snapshot by git, they can be edited, rolled back, or staged. Untracked files weren't in the last snapshot and are not currently in the staging area. After cloning a repo all files have the tracked status and are unmodified.

### Life Cycle of File Status
Editing a file marks it as modified, because its been changed since the last commit, then add stages the file so you can commit it.
![This](https://blog.udemy.com/wp-content/uploads/2015/08/image006.png)
Where the files are in this process seems to be observable with ```git status```

### Tracking and Staging a New File
```
git add filename
```
Tracks filename
```
git add *
```
Tracks all files in the repo
These commands set files to tracked, and stages them for committing.
Using ```git status``` gives info on changes to be committed on tracked files.

### Committing a File
To commit files that you've already added
```git commit -m "this is your commit message"```
Commit messages are nice. Make good ones.

### Committing All Changes
```git commit -a```
I don't understand how this is different really.

### Pushing Changes
This merges your branch with the remote repository, essentially makes your changes official.
```git push origin main```
Press the believe button for origin main for now.

### Stashing Changes
To rollback changes you haven't committed, but also save them use ```git stash``` This removes and hides changes. To restore your changes, use ```git stash apply```

## Remote Repositories
These are repositories online or on a network, such as GitHub.

### Cloned Repositories
For cloned repos Git gives the name origin to the origin server, and main to your local branch.

### Seeing Your Remotes
```git remote``` shows you short names like "origin," of all specified remote handles.
```git remote -v``` views remote URLs by their corresponding short names.
