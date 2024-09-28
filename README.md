# Git Basics
This guide provides a quick reference for common Git commands, which are useful for version control in software development.

## Git Initialization
Before you can start using Git in a project, you need to initialize a repository.
<br>
bash<br>
Copy code

```ruby
git init
```
Example:
<br>

bash<br>
Copy code
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
bash<br>
Copy code

```ruby
git status
```
for short for
Example:
<br>

bash<br>
Copy code
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
bash<br>
Copy code

```ruby
git log
```
Example:
<br>
bash<br>
Copy code

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
bash<br>
Copy code

```ruby
git add <file>
```
Example:
<br>
bash<br>
Copy code

```ruby
$ git add file.txt
```
To stage all modified files, you can use:
<br>
bash<br>
Copy code

```ruby
git add .
```
## Committing Changes
Once you've staged your changes, you can commit them to the repository:
<br>
bash<br>
Copy code

```ruby
git commit -m "Commit message"
```
Example:
<br>
bash<br>
Copy code

```ruby
$ git commit -m "Added a new feature"
```
Commit All Changes
<br>
To commit all changes (both tracked and untracked files) without explicitly using git add:
<br>
bash<br>
Copy code

```ruby
git commit -a -m "Commit message"
```
Example:
<br>
bash<br>
Copy code

```ruby
$ git commit -a -m "Fixed all bugs and added documentation"
```

## Viewing the Reflog
The reflog shows a history of all changes made to the tip of branches in your repository.
<br>
bash<br>
Copy code

```ruby
git reflog
```
Example:
<br>
bash<br>
Copy code

```ruby
$ git reflog
1d2a4d HEAD@{0}: commit: Added a new feature
d6e9f1 HEAD@{1}: commit: Initial commit
```
## Resetting Changes
You can reset changes to a previous commit using:
<br>
bash<br>
Copy code

```ruby
git reset --hard <commit>
```
Example:
<br>
bash<br>
Copy code

```ruby
$ git reset --hard d6e9f1
HEAD is now at d6e9f1 Initial commit
```
This command resets your repository to the specified commit, discarding all changes after it.

## HEAD Traverse
HEAD refers to the current position of your branch. You can move HEAD to a previous commit:
<br>
bash<br>
Copy code

```ruby
git checkout <commit>
```
Or simply move one commit back:
<br>
bash<br>
Copy code

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
bash<br>
Copy code

```ruby
$ git checkout HEAD^
```
Branch Management
To list all branches in your repository:

bash<br>
Copy code

```ruby
git branch
```
To create a new branch:
<br>
bash<br>
Copy code

```ruby
git branch <branch-name>
```
To switch to an existing branch:
<br>
bash<br>
Copy code

```ruby
git checkout <branch-name>
```
To create and switch to a new branch in one command:
<br>
bash<br>
Copy code

```ruby
git checkout -b <branch-name>
```
Example:
<br>
bash<br>
Copy code

```ruby
$ git branch feature-login
$ git checkout feature-login
```
## Viewing Commit Details (git show)
To view details about a specific commit:
<br>
bash<br>
Copy code

```ruby
git show <commit>
```
Example:
<br>
bash<br>
Copy code
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
