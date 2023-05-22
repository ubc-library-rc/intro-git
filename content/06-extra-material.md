---
layout: default
title: Extra Material
nav_order: 9
nav_exclude: false
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
 - TOC
{:toc}
</details>


In this workshop, we only showed the basic features of Git. Git and GitHub have many more features. Here, we list a few of them:

## GitHub and Visual Studio Code

Visual Studio Code has integrated source control management and support Git. You can also install other source control providers through VS Code Extension Marketplace.

The source control icon on the Activity Bar indicates an overview of the changes in the current repository. You can also open it using Ctrl + Shift + G shortcut. If you do not have a repository, you should create one first. The Introduction to Git and GitHub workshop covers the basics of Git and how to sync your local repository with GitHub.

In VS Code, you can stage and commit changes using the graphical user interface or by the terminal.

## Graphical user interface for Git

Some terminal shells use some simple graphics to communicate a great deal of information about the current status of your git repository. 

**Zsh** is highly customizable and **Oh My Zsh** is a community-driven framework that provides lots of plugins and themes to enhance your command line experience. For example, you can view the state of your Git repository right inside the terminal. You can install Oh My Zsh [here](https://ohmyz.sh/#install).

![Zsh with agnoster theme](https://ubc-library-rc.github.io/intro-development-environment/content/images/Zsh-with-agnoster-theme.jpg)

*Zsh with agnoster theme*

### Example: Source Control with VS Code
{: .no_toc}

To use source control tools in VS Code, you need to install Git on your machine. You can download the latest version on Git Website. When VS Code detects a Source Control Management Provider, it will show the git repository automatically and any changes will be displayed in the Activity Bar.

To track a project, you only need to click on the git symbol in the Activity Bar and initialize a repository. When you add a .gitignore file to your repository, VS Code automatically updates the visual indicator for files that you want to be tracked and filters out the files that you want to ignore.

If you click on any files in the Source Control view, VS Code will show a diff, which compares the new file with the old file in your repository and flags the changes. You can stage and commit changes one by one or all at once using the buttons available in the Source Control view.

You can push the local repository to GitHub using the Push or Push to… commands in the Source Control view. If you cloned the repository before, Push command syncs the local changes. If you want to build a new repository and push changes, use Push to… command.

You can create and checkout branches directly within VS Code by selecting Git: Create Branch and Git: Checkout to commands in the Command Palette. After running Git: Checkout to, you will see a dropdown list containing all of the branches and tags in the current repository. You can also create a new branch in the dropdown list.

If you have a Source Control Management Provider in the workspace, Git Status Bar will be added to the Status Bar that shows the current checked-out branch. You can Publish the current branch to a remote or Synchronize Changes which will pull remote changes down to your local repository and then push local commits to the upstream branch. To learn more about the capabilities of Git Extension in VS Code, check out the Source Control in VS Code webpage.



## Another Exercise: 

## Collaborating on GitHub

For the next step, get into pairs.  One person will be the "Owner" and the other
will be the "Collaborator". The goal is for the Collaborator to add changes into
the Owner's repository. If there is time we will switch roles at the end so everyone can play Owner and Collaborator.

First the Owner needs to give the Collaborator access to their repository.
Navigate to your repository On GitHub, click the settings button on the right,
then select Manage access. Click the green <em>Invite a collaborator</em> button and enter your partner's GitHub username in the search bar.

![Adding Collaborators on GitHub](figures/github-add-collaborators.png)

To accept access to the Owner's repo the Collaborator
needs to go to [https://github.com/notifications](https://github.com/notifications).

Next, the Collaborator needs to download a copy of the Owner's repository to their computer. This is called "cloning" a repository. To clone the Owner's "hello-world" repository onto
their `Desktop` the Collaborator would enter this command:

Input
{: .label .label-green}
~~~
$ git clone https://github.com/owner's-github-username/hello-world.git ~/Desktop/owner-hello-world
~~~

This creates a local copy of the owner's hello-world repository in a folder named <em>owner-hello-world</em>.  The collaborator can now make changes in their clone of the Owner's repository using the commands introduced earlier.

- use `cd` to navigate to the cloned repository
- use `touch` to create a new file in the repository
- add a few lines to the file using a text editor
- use `git add` to stage the file
- use `git commit -m "Commit note"` to commit the changes

Then push the Collaborator's change(s) to the *Owner's* repository on GitHub:

Input
{: .label .label-green}
~~~
$ git push origin main
~~~

Note that this time we didn't have to create a remote called `origin`: Git uses this
name by default when we clone a repository.  (This is why `origin` was a
sensible choice for a nickname earlier when we were setting up remotes by hand.)

Take another look to the Owner's repository on the GitHub website (you might need
to refresh your browser). You should be able to see the new commit made by the
Collaborator.

To download the Collaborator's changes from GitHub, the Owner now enters this command on their own computer:

Input
{: .label .label-green}
~~~
$ git pull origin main
~~~

Now the three repositories - Owner's local, Collaborator's local, and Owner's on
GitHub - are back in sync.

___Switch Owner and Collaborator roles if time permits and you'd like more practice___