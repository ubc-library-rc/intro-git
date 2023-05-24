---
layout: default
title: Concepts and tools
nav_order: 5
---

<p style="margin-bottom: 20px"></p>

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
 - TOC
{:toc}
</details>

## Git as a Version Control System

Version control system tracks the changes made to a group of files.  Version control systems like Git are often associated with software development but are increasingly used for collaboration in research and academic environments.. 

**Why use version control?**

Because no one wants to end up in this familiar place:

<p style="margin-top:20px;margin-bottom:20px">
<img src="figures/phd101212s.gif" width="300" style="margin-left:30px"/>
</p>

It takes some discipline to learn and make use of version control but there are many benefits:

* **Collaboration** - Version control helps teams work collaboratively on the same set of documents without interfering with each other. It allows for easy merging of changes made by different team members, helping to prevent conflicts and maintain a coherent codebase.  Git also facilitates code reviews, where team members can provide feedback and suggest improvements before merging changes.
* **Versioning** - It provides a thorough log of changes to tracked files without creating multiple copies, making it easier to identify the most current version. Git creates a timeline of commits, which are snapshots of your project at specific points.
* **Rolling back** - Made a mistake?  Version control lets you review and undo changes, reverting to previous stages in the document's history. This can be useful when changes to your files introduce unforeseen problems.
* **Understanding context** - Version control can help you understand how the code or writing came to be, who wrote or contributed particular parts, and who you might ask to help understand it better.
* **Backup** - By using Git, your codebase is stored locally on your machine as well as on remote repositories. This provides a built-in backup mechanism, reducing the risk of losing your code due to hardware failure or accidental deletions.
  
  
## What are Git and GitHub?
  
**_Git_** and **_GitHub_** are often used interchangeably but it's important to understand what each does and how they work together.

**_Git_** is a free and open-source tool that can be installed on your local computer to track changes made to a set of files (referred to as a "git repository" or "repo"). Git can be used independently to organize one's own work or to coordinate team projects with multiple authors. Git makes it easy to get a overview of all changes made to the file over time. Git keeps a list of changes made to the files of the project, thus, the earlier versions of each file are not overwritten and the developer can roll back to them.

Git also ensures that everyone's contributions are tracked and merged effectively by keeping copies of all previous versions and documenting the changes, including when they were made and who made the changes.    


Git was designed for _text_ files that can be opened in a text editor (as opposed to _binary_ file formats like .pdf and .docx).  A Git repository can preserve files of any type, but only text files will benefit from all Git's features.  
{: .info}

Git is developed in 2005 by [Linus Torvalds](https://github.com/torvalds), the famous creator of the Linux operating system kernel. A great number of software projects rely on Git for version control. 

[**_GitHub_**](https://github.com/) is a popular website for hosting and sharing Git repositories. GitHub provides an online infrastructure that makes it easier for teams to collaborate with Git.  Team members make contributions to the repository on local copies of the files, then "push" their changes back to GitHub so everyone else can see them.  

The GitHub interface makes it easy to view files in the repository and what changes have been made. GitHub also makes it easier for groups to publish their work (each GitHub repository can have its own project website, blog, and wiki using [GitHub Pages](https://pages.github.com/).)

[GitHub.ubc.ca](https://github.ubc.ca) is an instance of GitHub Enterprise supported by UBC for Educational use only. You can use UBC GitHub to collaborate on course materials with the support of a faculty member.
  
## Important terminal commands

Linux terminal, aka. command-line, console, or shell, is a text interface used to control a Linux computer. We need to know a few very useful commands in the terminal to use the features of Git as a command-line tool. Several graphical interfaces are available for Git as well, such as [GitHub Desktop](https://desktop.github.com/). For this workshop, you need the following commands:

<p style="margin-top:20px;margin-bottom:20px">
<img src="figures/coding.jpg" width="300" style="margin-left:30px"/>
</p>


Input
{: .label .label-green}
~~~
$ cd
~~~

To navigate through files and directories within a system, use the `cd` command followed by either the full path or the directory name. Running this command without a flag or option will take you to the home folder. Use `cd ..` to move to the parent directory (one directory up) and `cd -` to the previous directory.

Input
{: .label .label-green}
~~~
$ mkdir <new-directory>
~~~

This command creates one or multiple directories at once. You must have  permission to make a new folder in the parent directory. 

Input
{: .label .label-green}
~~~
$ ls
~~~

This command lists files and directories within a system and running it  without a flag or parameter will show the current working directory's content. With `ls -a`, hidden files will also be shown. The files created by Git in your Git repository are hidden and stored in `.git` directory.

Input
{: .label .label-green}
~~~
$ touch <new-file-name>
~~~

The `touch` command creates an empty file in the current directory. In this workshop, we use this command to make multiple empty files. You can use other methods to make empty files or copy files from other directories to populate your git folder.

Input
{: .label .label-green}
~~~
$ cat <file-name>
~~~

`cat` reads files and writes them on the screen. The name comes from its function to catenate files.