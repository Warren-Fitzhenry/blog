---
title: Common Git commands
date: "2019-02-01T22:40:32.169Z"
template: "post"
draft: false
slug: "Common git commands"
category: "Git"
tags:
  - "Git"
  - "Web Development"
description: "A list of common git commands with a short descriptions"
socialImage: "/media/42-line-bible.jpg"
---

Working with Git on the command line can be slightly daunting. To help with that, I’ve put together a list of common Git commands, what each one means, and how to use them. I will update this post as I go along!

Git with local repositories
git init
Git init initialises an empty git repository in the directory specified, allowing files within the directory to be added and committed.

```
git add < file name > # adds specified file to index
git add < subfolder > # adds specified directory to index
git add . # adds all unstaged files to index
git add --all # adds all unstaged files to index
```
Adds files or directories to the staging area, before they can be committed to the repository.

`git commit -m "message"`
Records the changes to the local repository. Each commit has a unique id. It is best practice to include a short message that describes the changes for easy reference. Once run, a short description of the changes will show up:

`1 file changed, 0 insertions(+), 0 deletions(-)`

To combine the add and commit commands, we can use:

`git commit -a -m "message"`

This will add all tracked files to the staging area and commit them.

`git log`
will return a log of all the commits in the repository

`git status`
gives information on the current branch, and lists any untracked changes in the directory.

```
git branch # lists all branches
git branch < branch name > # creates a new branch
git branch -d < branch name > # deletes a branch
```

To switch between branches we can use:

git checkout < branch name > # checkout a branch
git checkout -b < new branch name > # create and checkout a new branch
To merge different branches together, we can use git merge. For example, if I have a branch with a new feature on it < newfeature > and I would like to merge it into the < master > branch we can use:

## Merge changes from another branch into the current branch

```
git checkout master
git merge newfeature
Git with remote repositories
```

To clone a remote repository into our local directory, we can use the following command in the directory we want the repository to reside:

`git clone < remote repository name >`

By using git clone, git automatically remembers this connection and the remote as ‘origin’. To check this, type:

`git remote -v`

This will return two lines, the first being the ‘fetch URL’, which is used for reading access, and the second is the ‘Push URL’ which is used for writing access. It most cases, these will be the same.

```
Warren:main warrenfitzhenry$ git remote -v
origin	< remote repository > (fetch)
origin	< remote repository > (push)
```

Once connected, we can begin to pull from and push to the remote repository.

The git pull command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. 

```
git pull origin # updates local branch to the remote
git pull <remote branch name> <local branch name> 
```

Note that this is a combination of two commands – git fetch and git merge.

`git fetch` lets you see what the latest state of the remote repository is, without merging those changes locally.

`git push < local branch name >`
will push a local branch to the remote repository.