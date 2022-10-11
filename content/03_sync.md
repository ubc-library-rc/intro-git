---
layout: default
title: Syncing with GitHub
nav_order: 7
---

# Syncing with GitHub

So far you used Git to create a repository called "hello-world" on your own computer, but no one else can see those files.  Next you will use GitHub to share the contents of your repository so others can collaborate.  This involves creating an empty repository in GitHub, then linking it to your local repository.

## Create an empty GitHub repository

Log into your GitHub account and create a new repository by clicking the **+** icon in the upper-right corner of
any page, then selecting **New repository**.  

![add_new_repository](figures/add_new_repository.png)

- Name the repository "hello-world"
- Add optional description
- Ensure repository is set to "Public"
- Click "Create repository"

Though not mandatory, choosing a license is an important part of openly sharing your creative work online. For help selecting an appropriate license see <https://choosealicense.com/>.
{: .info}

## Linking your local repository to GitHub

After creating the "hello-world" repository GitHub will display the repository page.  This includes information required to link your GitHub repository, `remote`, to the repository you created with Git on your own computer.

You have two options to connect your local machine to Github. SSH is a security protocol widely used by many application. You can use the following commands to connect your newly created repository or your existing repository to Github. 

![The repository SSH on GitHub](figures/github-instructions-ssh.png)

You can also use HTTPS protocol to connect your local repository to Github. Take a look at the following figure and find the commands you need to use to sync your local repository with Github. We will explain these commands in the rest of this section.

![The repository HTTPS on GitHub](figures/github-instructions-https.png)


Note: Github removed password authentication on August 13, 2021. SSH is a secure way to connect your local machine to Github. To use the SSH protocol, we need a little more setup before we can actually connect to the remote repository. To find out more about the SSH authentication, check out [this page](content/06-extra-material.html). In this workshop, we are going to use the HTTPS protocol and Github access tokens. The latter is simpler but should be used with cautious. 

### Step 1: link the repositories with "git remote add"
Enter the command below, replacing <your_github_username> as appropriate.

Input
{: .label .label-green }
~~~
$ git remote add origin https://github.com/<your_github_username>/<github-repository-name>.git 
~~~
{: .language-bash }

This links your local Git repository to a _remote_ one. The link indicates the location of the remote repository, which is nicknamed _origin_ in this example.  The nickname can be anything but Git convention is to refer to the remote repository as "origin".  

We can confirm that it is set up correctly with this command:

Input
{: .label .label-green }
~~~
$ git remote -v
~~~

Output
{: .label .label-yellow }
~~~
origin  https://github.com/<your_github_username>/<github-repository-name> (fetch)
origin  https://github.com/<your_github_username>/<github-repository-name> (push)
~~~

### Step 2: synchronize the repositories with "git push"**

The `git push` command can "push" our local content and tracking information to the GitHub repository, synchronizing the content. If you run `git push` right now, Git asks for your Github username and password. Even if you enter the correct username and password, the command will not work since support for password authentication was removed in 2021. To fix this error, you can use Github Access Tokens or use code editors that support API authentication. In this workshop, we use access tokens:

#### Configure Access Token on Github

You can use token-based authentication when performing Git operations requiring authentication.

In the first step, we will create a personal Access Token on Github. Follow these steps for create one for your Github account:

* Click on your **Github profile icon** on the top right corner and click on **Settings**
* Choose **Developer Settings** on the menu on the left
* Click **Personal access tokens** and **Generate new token**]* Add a specific note that will help you identify the scope of the access token
* **Choose the Expiration period** from the drop down menu and select the scopes you want to grant the corresponding access to the generated access token. Make sure to select the minimum required scopes. For this workshop, `public_repo` should be enough.
* Click on **Generate Token**

Now, a new page is openned in which you can see your personal access token and copy it.

Now, we need to run the following command to use this access token:

Input
{: .label .label-green }
~~~
$ git remote set-url origin https://<github-token>@github.com/<username>/<repository-name>.git
~~~

Now, we have successfully configured token-based authentication and established a connection between the two repositories. To synchronize the content of the remote and local repositories, we will have to "push" our local changes to the Github repository.

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
~~~

The nickname of our remote repository is "origin" and the default local branch name is "main".
The `-u` flag tells git to remember these parameters, so that next time we can simply run `git push`
and Git will know what to do.

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

If you add a readme file or license file to your Github repository, the commit on Github is ahead of your latest commit on the local main branch and you need to pull the latest changes to sync the two repositories:


## Pulling changes

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