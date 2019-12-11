---
layout: default
title: Git basics
parent: Lesson plan
nav_order: 2
---

## Git basics

One of the challenges of learning Git is becoming familiar with its terminology and command structure. Git commands consist of verbs such as `add`, `commit`, and `push` preceded by the word `git`.  These base commands are often followed by arguments that provide more information about how and where Git should act.

The best way to learn a langauge is through practice.  In this workshop we will use Git to setup a new version-controlled project.

### Creating a repository

You can think of a **repository** as a group of files that Git tracks.  When you create a repository Git generates a hidden directory named `.git` in the same folder. Information about the repository, changes to the files, and previous versions are all stored in this hidden directory so they are accessible but don't get in the way.

You can create repositories using [GitHub's web interface](https://github.com/new), or on your own computer using the command line.  Let's use the command line to create a Git repository for new project.

First, create a directory called `hello-world` and navigate to the new directory.

Input
{: .label .label-green}
~~~
$ mkdir hello-world
$ cd hello-world
~~~

If you're not sure you're in the right place use the command "pwd" (print working directory) to display the complete path of your current directory.
{: .info}

We will now create a Git repository to track changes to our project.  Use the git **init** command, 
which is simply short for *initialise*.

Input
{: .label .label-green}
~~~
$ git init
~~~
Output
{: .label .label-yellow}
~~~
Initialized empty Git repository in <your file path>/hello-world/.git/
~~~

Your `hello-world` directory is now a git repository. 

If you run the "ls" command to list the contents of the "hello-world" 
directory your repository may seem empty.  But running "ls -a" instead will include hidden files in the list, revealing the new hidden directory named ".git".
{: .info}


### Displaying project status

The `git status` command displays the current state of a project.

Input
{: .label .label-green}
~~~
$ git status
~~~

Output
{: .label .label-yellow}
~~~
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
~~~

The output introduces two new Git concepts:
- "branch master" (explain what it is)
- "commit" (explain what it is)


### Adding and committing

We will now create and save our first project file. This is a two-stage process. First, we **add** any files for which 
we want to save the changes to a staging area, then we **commit** those changes to the repository. This two-stage 
process gives us fine-grained control over what should and should not be included in a particular commit.

Let's create a new file using the `touch` command, which is a quick way to create an empty file.

Input
{: .label .label-green}
~~~
$ touch index.md
~~~


The `.md` extension is for text files written using Markdown, a lightweight markup language with plain text formatting syntax. For more on Markdown see (link to Markdown resource, add .md cheatsheet to resources list)

Let's check the status of our project again.

Input
{: .label .label-green}
~~~
$ git status
~~~

Output
{: .label .label-yellow}
~~~
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    index.md

nothing added to commit but untracked files present (use "git add" to track)
~~~

Git has noticed a new file in our directory that we are not yet tracking. With colourised 
output, the filename will appear in red. To change this, and to tell Git we want to track any changes we make to 
index.md, we use `git add`.

Input
{: .label .label-green}
~~~
$ git add index.md
~~~


This adds our Markdown file to the **staging area** (the area where git checks for file changes). To confirm this we want to use `git status` again.

Input
{: .label .label-green}
~~~
$ git status
~~~

Output
{: .label .label-yellow}
~~~
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

    new file:   index.md
~~~


If we are using colourised output, we will see that the filename has changed colour (from red to green). Git also tells us that there
is a new file to be committed but, before we do that, let's add some text to the file.

We will open the file `index.md` with any text editor we have at hand (e.g. Notepad on Windows or TextEdit on Mac OSX) and enter `# Hello, world!`. The
hash character is one way of writing a header with Markdown. Now, let's save the file within the text editor and check if Git
has spotted the changes.

Input
{: .label .label-green}
~~~
$ git status
~~~

Output
{: .label .label-yellow}
~~~
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   index.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   index.md
~~~


This lets us know that git has indeed spotted the changes to our file, but that it hasn't yet staged them, so let's add 
the new version of the file to the staging area.

Input
{: .label .label-green}
~~~
$ git add index.md
~~~


Now we are ready to  **commit** our first changes. 
Commit is similar to 'saving' a file to Git. 
However, compared to saving, a commit provides a lot more information about the changes we have made,
and this information will remain visible to us later.

Input
{: .label .label-green}
~~~
$ git commit -m 'Add index.md'
~~~

Output
{: .label .label-yellow}
~~~
[master (root-commit) e9e8fd3] Add index.md
 1 file changed, 1 insertion(+)
 create mode 100644 index.md
~~~


We can see that one file has changed and that we made one insertion, which was a line with the text '#Hello, world!'. 
We can
also see the commit message 'Add index.md', which we added by using the `-m` flag after `git commit`.
The commit message is used to record a short, descriptive, and specific summary of what we did to help us remember later on without having to look at the actual changes.
If we just run `git commit` without the `-m` option, Git will launch nano (or whatever other editor we configured as `core.editor`)
so that we can write a longer message.

Having made a commit, we now have a permanent record of what was changed,
along with metadata about who made the commit and at what time.

> ## More on the Staging Area
>
> If you think of Git as taking snapshots of changes over the life of a project,
> `git add` specifies *what* will go in a snapshot
> (putting things in the staging area),
> and `git commit` then *actually takes* the snapshot, and
> makes a permanent record of it (as a commit).
> If you don't have anything staged when you type `git commit`,
> Git will prompt you to use `git commit -a` or `git commit --all`,
> which is kind of like gathering *everyone* for the picture!
> However, it's almost always better to
> explicitly add things to the staging area, because you might
> commit changes you forgot you made. (Going back to snapshots,
> you might get the extra with incomplete makeup walking on
> the stage for the snapshot because you used `-a`!)
> Try to stage things manually,
> or you might find yourself searching for "git undo commit" more
> than you would like!
{: .callout}

![The Git Staging Area](figures/git_staging_area.svg)

At the moment, our changes are only recorded locally, on our computer. If we wanted to 
work collaboratively with someone else they would have no way of seeing what we've done.
We will fix that in the next episode by using GitHub to share our work.
