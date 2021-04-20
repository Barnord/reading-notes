CVCS, or Centralized Version Control System, these systems have a single server that logs all changes and versions of uploaded files. GitHub is a DVCS, which is similar, except clients can clone repositories, which can be placed back on the server in the event any data is lost, which addresses the failure point of the CVCS. Git stores snapshots, every time you save, or commit files, Git saves the save with a reference. In the event of data loss, or corruption, you can access your old saves through Git. Through committing individual files, Git allows for non-linear development via many branches.


###### Importing
- git init
- git add*.c
- git add license
- git commit -m "commit notes go here"
I don't understand any of this yet

###### Cloning
-git clone (address from the button on the git site) (name of directory you want it in, defaults to repository name if empty) = this copies all versions of all the files for the cloned project. Also retrieves a copy of the newest version of the project.


##### Workflow

###### Local Repository Structure
A local Git repo has 3 components
1. Working Directory
2. Index
3. Head

