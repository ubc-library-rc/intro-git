---
layout: default
title: Additional resources
nav_order: 10
---

## Basic reference

### Navigating the shell

`pwd`
: print working directory

`ls`
: list contents of directory

`cd`
: change directory


### Interacting with files

`mkdir`
: make directory

`cat`
: send file or files to output (in most cases, print to shell)

`head`
: output first parts of a file or files

`tail`
: output last parts of a file or files

`mv`
: rename or move a file or files. Syntax for renaming a file: `mv FILENAME NEWFILENAME`

`cp`
: copy a file or files. Syntax: `cp FILENAME NEWFILENAME`

`>`
: redirect output. Syntax with `cat`: `cat FILENAME1 FILENAME2 > NEWFILENAME`

`rm`
: remove a file or files. *USE WITH CAUTION!!!*

### Git commands

Git cheat sheets:

* [GitHub git cheat sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)
* [Tower client git cheat sheet](https://www.git-tower.com/blog/git-cheat-sheet/)

`git init`
: create a new local git repository

`git status`
: view the status of your files in the working directory and staging area

`git add`
: tell git to start tracking a file, or a series of files

`git commit`
: save file changes from the staging area permanently to the project history

`git push`
: upload all commits to a remote repository, such as GitHub

`git log`
: show history of commits in reverse chronological order

`git diff`
: show changes made to tracked files

`git pull`
: download upstream changes and merge them into your local repository

`git remote add origin`
: add a remote repository named 'origin', to upload changes to or download changes from


## Further reading

* The GitHub [help pages](https://help.github.com/) are a good place to start
* GitHub has '[activities](https://guides.github.com/activities/hello-world/)' which aim to explain how git works
* GitHub also has interactive tutorials for their [online version (Learning Labs)](https://lab.github.com/) and for [using Git offline (Git-It)](https://github.com/jlord/git-it-electron#git-it-desktop-app)
* Atlassian has in depth and clear [tutorials](https://www.atlassian.com/git/tutorials) on using Git
