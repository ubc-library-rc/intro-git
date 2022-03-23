---
layout: default
title: Syncing with GitHub
parent: Workshop Content
nav_order: 3
---

## Syncing with GitHub
So far you used Git to create a repository called "hello-world" on your own computer, but no one else can see those files.  Next you will use GitHub to share the contents of your repository so others can collaborate.  This involves creating an empty repository in GitHub, then linking it to your local repository.

### SSH Background and Setup
We need to set up a way for our local computer to authenticate with GitHub so that GitHub recognizes our computer as belonging to the same person who owns the GitHub repository. 

We will use SSH as our authentication method. SSH stands for Secure SHell protocol.  SSH is a cryptographic network protocol that allows secure communication between computers using an otherwise insecure network.

What we will do now is the minimum required to set up the SSH keys and add the public key to a GitHub account.

<!-- > ## Advanced SSH -->
<!-- > A supplemental episode in this lesson discusses SSH and key pairs in more depth and detail.-->
<!-- {: .callout}-->

The first thing we are going to do is check if this has already been done on the computer you’re on.  

> ### Keeping your keys secure
> You shouldn't really forget about your SSH keys, since they keep your account secure. It’s good
>  practice to audit your secure shell keys every so often. Especially if you are using multiple
>  computers to access your account.
{: .callout}

We will run the list command (`ls`) to check what key pairs already exist on your computer. 
In our command we use the `~` as the shorthand for "my home directory."

~~~
ls -al ~/.ssh
~~~
{: .language-bash}


If you have not set up SSH, your output might look like this:

~~~
ls: cannot access '/c/Users/YourName/.ssh': No such file or directory
~~~
{: .output}

If SSH has been set up on the computer you're using, the public and private key pairs will be listed. The file names are either `id_ed25519`/`id_ed25519.pub` or `id_rsa`/`id_rsa.pub` depending on how the key pairs were set up.

If you do not have SSH set up, let's set it up now. Use this command to create key pairs:

~~~
$ ssh-keygen -t rsa -C "yourname@domain.name"
~~~
{: .language-bash}

~~~
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/YourName/.ssh/id_ed25519):
~~~
{: .output}

We want to use the default file, so just press <kbd>Enter</kbd>.

~~~
Created directory '/c/Users/YourName/.ssh'.
Enter passphrase (empty for no passphrase):
~~~
{: .output}

Your computer is now asking you for a passphrase to protect this SSH key pair. We recommend that you use a passphrase and that you make a note of it. There is no "reset my password" option for this setup. If you forget your passphrase, you have to delete your existing key pair and do this setup again. It's not a big deal, but easier if you don't have to repeat it. 

~~~
Enter same passphrase again:
~~~
{: .output}

After entering the same passphrase a second time, you will receive the confirmation

~~~
Your identification has been saved in /c/Users/YourName/.ssh/id_ed25519
Your public key has been saved in /c/Users/YourName/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:SMSPIStNyA00KPxuYu94KpZgRAYjgt9g4BA4kFy3g1o yourname@domain.name
The key's randomart image is:
+--[ED25519 256]--+
|^B== o.          |
|%*=.*.+          |
|+=.E =.+         |
| .=.+.o..        |
|....  . S        |
|.+ o             |
|+ =              |
|.o.o             |
|oo+.             |
+----[SHA256]-----+
~~~
{: .output}

The "identification" is actually the private key. You should never share it.  The public key is appropriately named.  The "key fingerprint"
is a shorter version of a public key.


Now we need to give our public key over to GitHub.

First, we need to copy the public key.  Be sure to include the `.pub` at the end, otherwise you’re looking at the private key.

~~~
cat ~/.ssh/id_rsa.pub
~~~
{: .language-bash}

~~~
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDmRA3d51X0uu9wXek559gfn6UFNF69yZjChyBIU2qKI yourname@domain.name
~~~
{: .output}

Copy that entire line of output, and we will paste the copied text into GitHub in the next step.

Now, going to GitHub.com, click on your profile icon in the top right corner to get the drop-down menu.  Click "Settings," then on the
settings page, click "SSH and GPG keys," on the left side "Account settings" menu.  Click the "New SSH key" button on the right side. Now,
you can add the title (A person might use the title "My 2021 work laptop," just a little description to remind themselves which computer this public key connect to). 
Paste your SSH key into the field, and click the "Add SSH key" to complete the setup.

Now that we’ve set that up, let’s check our authentication from the command line.
~~~
$ ssh -T git@github.com
~~~
{: .language-bash}

~~~
Hi YourName! You've successfully authenticated, but GitHub does not provide shell access.
~~~
{: .output}

### Create an empty GitHub repository

Log into your GitHub account and create a new repository by clicking the **+** icon in the upper-right corner of
any page, then selecting **New repository**.  

![add_new_repository](figures/add_new_repository.png)

- Name the repository "hello-world"
- Add optional description
- Ensure repository is set to "Public"
- Click "Create repository"

Though not mandatory, choosing a license is an important part of openly sharing your creative work online. For help selecting an appropriate license see <https://choosealicense.com/>.
{: .info}

### Linking your local repository to GitHub

After creating the "hello-world" repository GitHub will display the repository page.  This includes information required to link your GitHub repository to the "hello-world" repository you created with Git on your own computer.     

We will use the Secure Shell (SSH) protocol for this lesson, so please make sure that button shows that it is selected and that the address in the text box starts with git@github. It will look something like this:

![The repository SSH on GitHub](figures/repository_ssh1.png)

On the same page GitHub provides instructions to "push an existing repository from the command line."  We will use these commands to synchronize our repositories:

![GitHub instructions](figures/github-instructions-ssh.png)

**Step 1: link the repositories with "git remote add"**
Enter the command below, replacing <your_github_username> as appropriate.

Input
{: .label .label-green }
~~~
$ git remote add origin git@github.com:yourname/hello-world.git 
~~~
{: .language-bash }

This links your local Git repository to a _remote_ one. The SSH indicates the location of the remote repository, which is nicknamed _origin_ in this example.  The nickname can be anything but Git convention is to refer to the remote repository as "origin".  

We can confirm that it is set up correctly with this command:

Input
{: .label .label-green }
~~~
$ git remote -v
~~~

Output
{: .label .label-yellow }
~~~
origin  https://github.com/<your_github_username>/hello-world (fetch)
origin  https://github.com/<your_github_username>/hello-world (push)
~~~


**Step 2: synchronize the repositories with "git push"**
The `git push` command can "push" our local content and tracking information to the GitHub repository, synchronizing the content.

Input
{: .label .label-green }
~~~
$ git push -u origin main
~~~

Output
{: .label .label-yellow }
~~~
Counting objects: 3, done.
Writing objects: 100% (3/3), 226 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/<your_github_username/hello-world
 * [new branch]      main -> main
Branch main set up to track remote branch main from origin.
~~~

The nickname of our remote repository is "origin" and the default local branch name is "main".
The `-u` flag tells git to remember these parameters, so that next time we can simply run `git push`
and Git will know what to do.

You may be prompted to enter your GitHub username and password to complete the command.

When we do a `git push` we will see Git "pushing" changes to the specified remote repository - in this case, on GitHub. Because our file is small this happens instantly, but it may take longer if you made many changes or are adding a very large repository.  The `git status` command will indicate the status after "pushing" is complete.  


Input
{: .label .label-green }
~~~
$ git status
~~~

Output
{: .label .label-yellow }
~~~
On branch main
Your branch is up-to-date with 'origin/main'.
nothing to commit, working tree clean
~~~

This output lets us know where we are working (the main branch). We can also see that we have no changes to commit, and you'll find a copy of the "index.md" file in your GitHub "hello-world" repository.

### Pulling changes

When working with others or on multiple computers we need a way to pull all the remote changes back into our local repository. We can see how this works by adding a file to our GitHub repository, then "pulling" that change back to our computer.

Near the bottom of the "hello-world" repository on GitHub there is a button to "Add a README" file to your repository. Click the button, enter some text, then scroll to the bottom and click "Commit new file" (The default commit message will be "Create README.md", which is fine for our purposes).

It is good practice to add a README file briefly describing what the project is about. If the README is in the root directory GitHub will automatically display it like a cover page for your repository.
{: .info}

After adding a README on GitHub your local repository is out-of-sync with the remote repository.  Let's fix that by pulling the remote changes into local repository with `git pull`.

Input
{: .label .label-green }
~~~
$ git pull
~~~

Output
{: .label .label-yellow }
~~~
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/<your_github_username>/hello-world
   8e2eb99..0f5a7b0  main     -> origin/main
Updating 8e2eb99..0f5a7b0
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
~~~


The output shows that we have fast-forwarded our local repository to include the file README.md. We could confirm
this by entering the `ls` command.

This section introduces some basic git commands but there are many others that may be useful in more complex and collaborative projects. For a more detailed introduction see the the online Software Carpentry course [Version control with Git](https://swcarpentry.github.io/git-novice/).

### Reviewing local changes

The `git diff` command shows the changes we have made before a commit. To test this, open "index.md" with any text 
editor and enter a new line of text (in this example we added "It's a beautiful rainy day" on the second line of "index.md").  Save the file, then use `git diff` to see the changes.

Input
{: .label .label-green }
~~~
$ git diff
~~~

Output
{: .label .label-yellow }
~~~
diff --git a/index.md b/index.md
index aed0629..989787e 100644
--- a/index.md
+++ b/index.md
@@ -1 +1,2 @@
 # Hello, world!
+It's a beautiful rainy day
~~~


Here's what the output reveals:

- Line 1 tells us Git is comparing "a" and "b" versions of the index.md file
- Line 2 indicates which tracked versions "a" and "b" correspond to; "aed0629" and "989787e" are unique computer-generated identifiers for each version
- The last two lines show the changes to the "index.md" between the compared versions: 
    - there were no changes to the `# Hello, world!` line
    - a line was added with the text `It's a beautiful rainy day` ("+" indicates an addition and "-", a deletion)

We can now add and commit the updated version of "index.md":

Input
{: .label .label-green }
~~~
$ git add index.md
$ git commit -m 'Add note about the weather'
~~~

The `git log` command provides another way to view past activity in our git repository.

Input
{: .label .label-green }
~~~
$ git log
~~~

Output
{: .label .label-yellow }
~~~
commit 8e2eb9920eaa0bf18a4adfa12474ad58b765fd06
Author: Your Name <your_email>
Date:   Mon Jun 5 12:41:45 2017 +0100

    Add note about the weather

commit e9e8fd3f12b64fc3cbe8533e321ef2cdb1f4ed39
Author: Your Name <your_email>
Date:   Fri Jun 2 18:15:43 2017 +0100

    Add index.md
~~~


`git log` lists information about all commits in reverse chronological order, including the commit messages we wrote to describe them. It is important to add meaningful commit messages, especially when working on teams.  Best practice is to write commit messages in the imperative (e.g. 'Add index.md' instead of 'Adding index.md').

### Keeping Git and GitHub in sync

Take another look at your "hello-world" repository on GitHub.  The "index.md" ifle is there, but there is only one commit.

![Only one commit on GitHub](figures/github-one-commit.png)

If you click on the "index.md" file you will see that it contains the "Hello, world!" header but not our new line about the weather.  This is because we haven't pushed our most recent local changes to the remote repository.  Do so now using the `git push` command.

Input
{: .label .label-green }
~~~
$ git push
~~~

Output
{: .label .label-yellow }
~~~
Counting objects: 3, done.
Writing objects: 100% (3/3), 272 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/<your_github_username>/hello-world
   e9e8fd3..8e2eb99  main -> main
~~~

Checking GitHub again shows 2 commits, the same as in our local repository.


