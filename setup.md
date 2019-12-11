---
layout: default
title: Setup
---

## Pre-workshop setup 
Please bring a laptop with the Bash Shell and Git installed **before** the workshop.

If you do not have access to a laptop or have difficulty meeting these prerequisites please contact jeremy.buhler@ubc.ca.  We will do our best to ensure everyone can participate.
{: .info }

### 1. Create a free [GitHub account](https://github.com)

### 2. Install the Bash Shell and Git
- **Mac** and **Linux**. Bash is already installed (no action required). Install Git using [these instructions](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
- **Windows**. Follow these instructions to download the Bash Shell and Git at the same time (a [Video Tutorial](https://www.youtube.com/watch?v=339AEqk9c-8) is also available).
    1. Download the Git for Windows [installer](installer).
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

### 3. Configure Git user name and email
Open a terminal window and enter the following commands to configure Git:

~~~
$ git config --global user.name "Your Name"
$ git config --global user.email "your@email"
~~~

This is only required once. Your user name and email will be recorded with each change you make to documents tracked with Git. The email address should be the same one you used when setting up your GitHub account.

### 4. Set your preferred text editor
Git sometimes opens a text editor to complete a task. The default is the Vi/Vim text editor but most people will prefer to use something more familiar. The simplest options are `"notepad"` on Windows,  `"nano -w"` on Mac, and `"nano -w"` on Linux. 
This command will set your preferred editor to Notepad:

~~~
$ git config --global core.editor "notepad"
~~~
