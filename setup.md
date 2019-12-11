---
layout: default
title: Setup
---

## Pre-workshop setup 
Please bring a laptop with the Bash Shell and Git installed **before** the workshop.

If you do not have access to a laptop or have difficulty meeting these prerequisites please contact jeremy.buhler@ubc.ca.  We will do our best to ensure that everyone is able to participate.
{: .note }

#### 1. Install the Bash Shell and Git
  - **Windows**. Follow [these instructions](https://carpentries.github.io/workshop-template/#shell) to download the Bash Shell and Git at the same time.
  - **Mac** and **Linux**. Bash is already installed (no action required). Install Git using [these instructions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

#### 2. Create a free [GitHub account](https://github.com)

#### 3. Configure Git user name and email
Open a terminal window and enter the following commands to configure Git:

~~~
$ git config --global user.name "Your Name"
$ git config --global user.email "your@email"
~~~

This is only required once. Your user name and email will be recorded with each change you make to documents tracked with Git.  

The email address should be the same one you used when setting up your GitHub account.
{: .warn}

#### 4. Set your preferred text editor
Git sometimes opens a text editor to complete a task. The default is the Vi/Vim text editor but most people will prefer to use something more familiar. The simplest options are `"notepad"` on Windows,  `"nano -w"` on Mac, and `"nano -w"` on Linux. 
This command will set your preferred editor to Notepad:

~~~
$ git config --global core.editor "notepad"
~~~
