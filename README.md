# Git Basics
This guide provides a quick reference for common Git commands, which are useful for version control in software development.

## Git Initialization
Before you can start using Git in a project, you need to initialize a repository.
<br>
 
 

```ruby
git init
```
Example:
<br>

 
 
<br>

```ruby
$ git init

Initialized empty Git repository in /path/to/repo/.git/
```
This command sets up a new Git repository in your current directory.

<br>

## Checking Git Status
To check the status of your working directory and see which files have changes that need to be staged or committed:
<br>
 
 

```ruby
git status
```
for short for
Example:
<br>

 
 
```ruby
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file.txt
```

## Viewing Git Log
To view the commit history of the repository:
<br>
 
 

```ruby
git log
```
Example:
<br>
 
 

```ruby
$ git log
commit 1d2a4d (HEAD -> main)
Author: John Doe <johndoe@example.com>
Date:   Mon Sep 28 10:00:00 2024 +0000

    Initial commit
```
## Staging Files (git add)
Before committing changes, you need to stage them using the git add command.
<br>
 
 

```ruby
git add <file>
```
Example:
<br>
 
 

```ruby
$ git add file.txt
```
To stage all modified files, you can use:
<br>
 
 

```ruby
git add .
```
## Committing Changes
Once you've staged your changes, you can commit them to the repository:
<br>
 
 

```ruby
git commit -m "Commit message"
```
Example:
<br>
 
 

```ruby
$ git commit -m "Added a new feature"
```
Commit All Changes
<br>
To commit all changes (both tracked and untracked files) without explicitly using git add:
<br>
 
 

```ruby
git commit -a -m "Commit message"
```
Example:
<br>
 
 

```ruby
$ git commit -a -m "Fixed all bugs and added documentation"
```

## Viewing the Reflog
The reflog shows a history of all changes made to the tip of branches in your repository.
<br>
 
 

```ruby
git reflog
```
Example:
<br>
 
 

```ruby
$ git reflog
1d2a4d HEAD@{0}: commit: Added a new feature
d6e9f1 HEAD@{1}: commit: Initial commit
```
## Resetting Changes
You can reset changes to a previous commit using:
<br>
 
 

```ruby
git reset --hard <commit>
```
Example:
<br>
 
 

```ruby
$ git reset --hard d6e9f1
HEAD is now at d6e9f1 Initial commit
```
This command resets your repository to the specified commit, discarding all changes after it.

## HEAD Traverse
HEAD refers to the current position of your branch. You can move HEAD to a previous commit:
<br>
 
 

```ruby
git checkout <commit>
```
Or simply move one commit back:
<br>
 
 

```ruby
git checkout HEAD^
```
or for parent of HEAD

```ruby
git checkout HEAD^^
```
or for parent of HEAD

```ruby
git checkout HEAD^2
```
Example:
<br>
 
 

```ruby
$ git checkout HEAD^
```
Branch Management
To list all branches in your repository:

 
 

```ruby
git branch
```
To create a new branch:
<br>
 
 

```ruby
git branch <branch-name>
```
To switch to an existing branch:
<br>
 
 

```ruby
git checkout <branch-name>
```
To create and switch to a new branch in one command:
<br>
 
 

```ruby
git checkout -b <branch-name>
```
Example:
<br>
 
 

```ruby
$ git branch feature-login
$ git checkout feature-login
```
## Viewing Commit Details (git show)
To view details about a specific commit:
<br>
 
 

```ruby
git show <commit>
```
Example:
<br>
 
 

```ruby
$ git show 1d2a4d
commit 1d2a4d (HEAD -> main)
Author: John Doe <johndoe@example.com>
Date:   Mon Sep 28 10:00:00 2024 +0000

    Added a new feature

diff --git a/file.txt b/file.txt
index e69de29..d95f3ad 100644
--- a/file.txt
+++ b/file.txt
@@ -0,0 +1,3 @@
+New content added to the file
```

# Working with Remote Repos

Cloning a Repository
Cloning a repository creates a local copy of a remote repository on your machine.

 
 
git clone <repository-url>
Example:<br>

 
 

```ruby
$ git clone https://github.com/username/repository.git
```

This command will download the entire project from the remote repository and create a local working directory.
<br>

## Managing Remote Repositories
### Adding a Remote
To link your local repository to a remote repository:
<br>
 
 

```ruby
git remote add <name> <remote-url>
```

Example:<br>

 
 

```ruby
$ git remote add origin https://github.com/username/repository.git
```
### Viewing Remote Repositories
To list all remote repositories linked to your local repository:
<br>
 
 

```ruby
git remote -v
```
Example:<br>

 
 

```ruby
$ git remote -v
origin  https://github.com/username/repository.git (fetch)
origin  https://github.com/username/repository.git (push)
```

### Removing a Remote
To remove a remote:
<br>
 
 

```ruby
git remote remove <name>
```

Example:<br>

 
 

```ruby
$ git remote remove origin
```

# Merging Branches
Git allows you to combine the changes from different branches using various types of merges. Before merging, ensure you are on the branch you want to merge into.
<br>

## I Fast-Forward Merge
If there are no diverging changes between branches, Git will simply move the branch pointer forward.
<br>


<p align="center">
  <img src="https://github.com/user-attachments/assets/3c0c763d-0fd1-4b9b-b807-3d5105bd2803" width="200" heigth="200">
</p>


<br>
 
 

```ruby
git merge <branch-name>
```
Example:<br>

 
 

```ruby
$ git checkout main
$ git merge feature-branch
```
If the feature-branch has all the commits ahead of main, Git performs a fast-forward merge.
<br>

to avoid Fast-forward merege:
<br>
 
 

```ruby
git merge --on-ff <branch-name>
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/4804d441-69d4-48e0-962b-b8bcd30a0934" width="200" heigth="200">
</p>


## II 3-Way Merge
If the branches have diverged, Git performs a 3-way merge, creating a merge commit.
<br>
 
 

```ruby
git merge <branch-name>
```
Example:<br>

 
 

```ruby
$ git checkout main
$ git merge feature-branch
```
Git will create a new merge commit combining changes from both branches.

## III Squash Merge
Squashing combines all commits from the feature branch into one commit on the target branch.
<br>
 
 

```ruby
git merge --squash <branch-name>
```
Example:<br>

 
 

```ruby
$ git checkout main
$ git merge --squash feature-branch
$ git commit -m "Merged feature-branch as a single commit"
```
## Conflict Resolution
If Git encounters conflicts during a merge, it will pause and mark the conflicting areas in the files. You need to manually resolve the conflicts and complete the merge.
<br>
 
 

```ruby
git status
```
Identify the files with conflicts, resolve them, then mark the files as resolved:
<br>
 
 

```ruby
git add <file>
git commit -m "Resolved merge conflicts"
```
# Pushing Changes
After making changes locally, you need to push them to the remote repository to share them with others.
<br>
 
 

```ruby
git push <remote> <branch-name>
```
Example:<br>

 
 

```ruby
$ git push origin main
```
This command pushes the local main branch to the origin remote repository.
<br>
If this is your first push to a remote branch:
<br>
 
 

```ruby
git push -u origin <branch-name>
```
Example:<br>

 
 

```ruby
$ git push -u origin feature-branch
```
This command sets origin/feature-branch as the default upstream branch.

# Pulling Changes
To update your local repository with the latest changes from the remote repository, use the git pull command:
<br>
 
 

```ruby
git pull <remote> <branch-name>
```
Example:<br>

 
 

```ruby
$ git pull origin main
```
This command fetches the changes from the remote main branch and merges them into your current branch.
