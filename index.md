---
layout: default
title: Setup
---
## Introduction to Git and GitHub
Learn the basics of using Git and GitHub for version control and collaboration.  Git is widely used version control software that tracks changes to a group of files, referred to as a repository.  GitHub is a popular website for hosting and sharing Git repositories, making it easier to collaborate and share your work.  Together, Git and GitHub provide a platform that is increasingly used for collaboration in research and academic environments.  

In this beginner workshop participants will learn key concepts, create their own Git repository, and publish to GitHub.  No previous experience with Git is required.  Familiarity with the command line interface will be helpful but is not necessary.

### Pre-workshop setup
Please bring a laptop with the Bash Shell and Git installed **before** the workshop.

If you do not have access to a laptop or have difficulty meeting these prerequisites please contact jeremy.buhler@ubc.ca.  We will do our best to ensure everyone can participate.
{: .info }

 **1. Create a free [GitHub account](https://github.com)**

 **2. Install the Bash Shell and Git**
- **Mac** and **Linux**. Bash is already installed (no action required). Install Git using [these instructions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
- **Windows**. The easiest pathway on Windows is to turn on "Windows Subsystem for Linux" following [these instructions](https://stackoverflow.com/questions/36352627/how-to-enable-bash-in-windows-10-developer-preview/36465000#36465000).

If you want to take a more manual route on Windows, follow these instructions to download the Bash Shell and Git at the same time (a [Video Tutorial](https://www.youtube.com/watch?v=339AEqk9c-8) is also available).
    1. Download the Git for Windows [installer](https://git-for-windows.github.io).
    2. Run the installer and follow the steps below:
        1. Click on "Next" four times (two times if you've previously installed Git). You don't need to change anything in the Information, location, components, and start menu screens.
        2. From the dropdown menu select "Use the nano editor by default" and click on "Next".
        3. Ensure that "Git from the command line and also from 3rd-party software" is selected and click on "Next". (If you don't do this Git Bash will not work properly, requiring you to remove the Git Bash installation, re-run the installer and to select the "Git from the command line and also from 3rd-party software" option.)
        4. Ensure that "Use the native Windows Secure Channel library" is selected and click on "Next".
        5. Ensure that "Checkout Windows-style, commit Unix-style line endings" is selected and click on "Next".
        6. Ensure that "Use Windows' default console window" is selected and click on "Next".
        7. Ensure that "Enable file system caching" and "Enable Git Credential Manager" are selected and click on "Next".
        8. Click "Install".
        9. Click "Finish".
    3. If your "HOME" environment variable is not set (or you don't know what this is):
        1. Open command prompt (Open Start Menu then type `cmd` and press "Enter"
        2. Type the following line into the command prompt window exactly as shown:
         `setx HOME "%USERPROFILE%"`
        3. Press "Enter." you should see `SUCCESS: Specified value was saved.`
        4. Quit command prompt by typing `exit` then pressing "Enter"

This will provide you with both Git and Bash in the Git Bash program.

 **3. Configure Git user name and email**  
Open Bash (_Terminal_ in Mac, _Git Bash_ in Windows) and enter the following commands to configure Git. (Note that `$` represents the command prompt; the commands themselves start with the word `git`.)

~~~
$ git config --global user.name "Your Name"
$ git config --global user.email "your@email"
~~~

This is only required once. Your user name and email will be recorded with each change you make to documents tracked with Git. The email address should be the same one you used when setting up your GitHub account.

 **4. (OPTIONAL) Set your preferred text editor**  
Git sometimes opens a text editor automatically so you can complete a task. The Git default is the Vi/Vim text editor, which some users may find difficult to use. To change the default text editor run the command below and indicate your preferred editor. This can be any text editor, but common choices are `"notepad"` on Windows and `"nano"` on Mac or Linux.

~~~
$ git config --global core.editor "notepad"
~~~
