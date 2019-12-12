---
layout: default
title: Syncing with GitHub
parent: Lesson plan
nav_order: 3
---

## Syncing with GitHub
So far you used Git to create a repository called "hello-world" on your own computer, but no one else can see those files.  Next you will use GitHub to share the contents of your repository so others can collaborate.  This involves creating an empty repository in GitHub, then linking it to your local repository.

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

We will need the GitHub repository URL, which will look something like this:

![The repository URL on GitHub](figures/repository-url.png)

On the same page GitHub provides instructions to "push an existing repository from the command line."  We will use these commands to synchronize our repositories:

![GitHub instructions](figures/github-instructions.png)

**Step 1: link the repositories with "git remote add"**
Enter the command below, replacing <your_github_username> as appropriate.

Input
{: .label .label-green }
~~~
$ git remote add origin https://github.com/<your_github_username>/hello-world.git
~~~

This links your local Git repository to a _remote_ one. The URL indicates the location of the remote repository, which is nicknamed _origin_ in this example.  The nickname can be anything but Git convention is to refer to the remote repository as "origin".  

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
$ git push -u origin master
~~~

Output
{: .label .label-yellow }
~~~
Counting objects: 3, done.
Writing objects: 100% (3/3), 226 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/<your_github_username/hello-world
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
~~~

The nickname of our remote repository is "origin" and the default local branch name is "master".
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
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
~~~

This output lets us know where we are working (the master branch). We can also see that we have no changes to commit, and you'll find a copy of the "index.md" file in your GitHub "hello-world" repository.

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
   e9e8fd3..8e2eb99  master -> master
~~~

Checking GitHub again shows 2 commits, the same as in our local repository.

### Pulling changes

When working with others or on multiple computers we need a way to pull all the remote changes back into our local repository. We can see how this works by adding a file to our GitHub repository, then "pulling" that change back to our computer.

Near the bottom of the "hello-world" repository on GitHub there is a button to "Add a README" file to your repository. Click the button, enter some text, then scroll to the bottom and click "Commit new file" (The default commit message will be "Create README.md", which is fine for our purposes).

It is good practice to add a README file briefly describing what the project is about. If the README is in the root directory GitHub will automatically display it like a cover page for your repository.
{: .info}

After adding a README on GitHub your local repository is now out of sync with the remote repository.  Let's fix that by pulling the remote changes into local repository using the `git pull` command.

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
   8e2eb99..0f5a7b0  master     -> origin/master
Updating 8e2eb99..0f5a7b0
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
~~~


The output shows that we have fast-forwarded our local repository to include the file README.md. We could confirm
this by entering the `ls` command.

This section introduces some basic git commands but there are many others that may be useful in more complex and collaborative projects. For a more detailed introduction see the the online Software Carpentry course [Version control with Git](https://swcarpentry.github.io/git-novice/).
