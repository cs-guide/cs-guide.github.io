---
tags:
  - Git
  - GitHub
---


**Git is for everyone.** 
Whether you're a software developer, digital artist, student, teacher or writer - 
you probably have some way to organize your projects and files on your computer.
Especially for larger and important projects you most likely create backups of your work
(else you'll probably regret it at some point).

I used to send backups to my email or save them on a USB stick. 
However, the problem with these types of backups is that they take quite some time if
you have to create them manually. As your project grows, this process will become even slower
and more error-prone since you might forget to include or exclude some files.

Because humans are lazy, you will simply skip or forget about backing up your files. 
It could also happen that you accidentally delete or edit files that you didn't mean to edit.
In case something goes wrong, these simple mistakes might cost you hours or even days of work.

You might also have local backups, creating a folder for each new version.
This could quickly lead to a nightmare like this:

![Image](/assets/img/test.PNG)

Also, what if you wanted to cooperate with someone else on your project?
If each of you would work on a different section of the project, collaboration could be pretty
stressful. In order to share updates with each other, you would have to send
new versions of the project via email or use a service like Dropbox or Google Drive.
But this way you will never have a complete picture of the current state of the project
since files are scattered everywhere on different computers.

There are certainly many more of these issues but it's time to focus on a solution.

# What is Git?

By now, you should have a basic understanding of what some of the most common problems are that
occur when working on a project that involves multiple files, versions or people.

Git is a system that aims to address these problems.
Let's have a look at how Git achieves this, briefly describing the solution for each issue:

- **Managing different versions of a project**:
Git is a widely-used version control system. This means it can be used to keep track of
different versions of a set of files. Git is also pretty smart about this: Instead of
saving the entire project for each new version, only the parts that were actually changed
will be saved. You can probably see how this can speed up your workflow a lot.

- **Undoing changes**:
Unless you forget to save your progress, you can easily undo changes (`commits`) that you did to
any files that were tracked by Git. This spares you from having to create local backups manually
and you will also have much finer control of to which point in the commit history you want to
revert back to.

- **Collaboration**:
The common Git workflow is centralized. This means you have one shared repository that all members of
a team can `push` changes to. You can create different branches representing different topics that
individuals can work on independently from the central branch (often called `master`).
The branches can then be merged back into the `master` branch so that others have the latest version
of the project available.


# The basic Git workflow

This is what the basic workflow will look like when working with Git:
1. Work on your project (either on the `master` or on a topic branch).
2. Add your changes to the staging area/index: `git add`
3. Commit your changes locally: `git commit`
4. Push your commits to a remote repository: `git push`
5. Repeat

## Getting started

Git is almost always used via the terminal. Especially if you're a Windows user this might seem 
unfamiliar at first but you will quickly learn to appreciate the simplicity. There are in fact several
GUI tools for Git but I would still advise starting with the command line as this gives you much more control. 

If you want to try this out on your computer right now, please refer to 
[this tutorial](https://www.atlassian.com/git/tutorials/install-git#windows) that describes
how to set up Git on your computer.

Let's look at the commands that you will use frequently. Open up a terminal in the 
root directory of your project (or create a new one) to follow along.

```
git init
```

In order for Git to be able to track your files you have to initialize a local repository.
All files that are in that directory or in a subdirectory are visible
to Git. The `init` command will automatically create a `.git` folder that contains all of the information
Git needs to know about your project. Git will also automatically set up a `master` branch that you can work on.

```
git status
```

The `status` command will become very handy to quickly see if anything has changed in your repository.
Therefore you should use it regularly. In a repository that does not contain any changed files the output of that
command should look something like this:

![Image](/assets/img/test2.png)

## Work on your project
Since our repository is pretty empty right now, let's add some files and run the `git status` command again:

![Image](/assets/img/test3.png)

As you can see Git recognized that the contents in the repository have changed. However, to actually save the changes
we made, we have to add the files to the staging area first. Let's do just that:

```
git add -A
```

The `-A` option adds *all* changes we made to the repository since the last commit to the index. 
You can also be more precise about which files you want to stage. If you want to find more about the `git add`
command, you can check out my blog post on exactly this topic: [Git Add Demystified]().

Running `git status` again will inform us about the changes we just made. This will show you files that were modified,
renamed, copied or deleted or which ones haven't been tracked yet. Any time you change a tracked file you have to readd it.
This may sound annoying but it prevents you from accidentally adding changes to the staging area that you didn't want to track.

![Image](/assets/img/test4.png)

If you decide you want to unstage any files that you might have accidentally added, you can run
`git rm --cached <file>` as the terminal message points out.

## Commiting your changes

Now it's time to bundle the changes you have previously made into a single commit. A commit will include all
files that are currently in the staging area. When using `git command` you will be asked to write a short message about
your commit:  

![Image](/assets/img/test5.png)

Don't neglect the commit message especially when collaborating with others (your future self will thank you as well)! 
People want to quickly see what a specific commit is all about. Therefore, you should briefly explain what changes you made and why.
In case you want to find out more about good commit messages, I'd highly recommend this article: 
[How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/).

**Tip:** To change the default text editor for your commit messages, type: `git config --global core.editor "path"` where
`path` is the absolute file path to the executable of your preferred text editor. For a shorter version of the `commit`
command without having to open an editor, use `git commit -m "Your commit message"` 
{: .notice--info}

# Working with remote repositories

Until now, you have used Git exclusively offline. But you probably want to store your projects somewhere else than on your local
machine (for backups and collaboration/distribution of your project). You could either set up your own Git server or simply
use an existing hosting site. The most popular one by far is GitHub which I will be using in this section.

GitHub has many features that simplify collaboration on a project and uses Git for version control.

Add GitHub description
{: .notice--danger}

## Getting started with GitHub

Head over to [GitHub](https://github.com/) and create a new user account or login with an existing one.
We'll start by creating a new repository (use the `New` button on the homepage or click [here](https://github.com/new)). 
Enter the name of your project and an optional description (you can easily change these later). Choose whether you want to share your repository with anyone to see or keep it private.

**Note:** GitHub recently changed their policy to provide free private repositories for everyone (limited to 3 contributors per
project). Previously this was only included in the paid plan.
{: .notice--info}

You can also add readme and license files or create them later.

![Image](/assets/img/test6.png)

When the repository has been created you should see some commands that Git recommends to setup your project. 
It's time to connect your local repository with GitHub.

## Connecting your local repository

We first have to add GitHub as a remote repository. You can copy the `git remote add origin` command from the previous GitHub page
and paste it into your terminal. Choose the HTTPS link for now and adapt the URL to your repo:

```
git remote add origin https://github.com/username/repo.git
```

Later I would recommend using the SSH URL (in the form `git@github.com:username/repo.git`). This way you won't have to enter your 
username and password every time you connect to GitHub. You can find more info about this 
[here](https://help.github.com/en/articles/which-remote-url-should-i-use).

This command adds the link to your GitHub repository to a list of remotes which you can then refer to by its name instead of 
having to use the full URL. The name of the remote doesn't matter but `origin` is the one that most people use.

![Image](/assets/img/test7.png)

**Tip:** If you accidentally entered the wrong link use the command `git remote remove origin` and readd the remote.
For a list of all your current remotes type `git remote -v`.
{: .notice--info}

## Pushing your work to GitHub

Now it's time to push your first commit to GitHub! Use the following command:

```
git push -u origin master
```

All your latest commits that you haven't uploaded yet will be pushed to the remote repository at GitHub.

![Image](/assets/img/test8.png)

The `-u` option will make your local `master` branch track the remote `master` branch, so the next time you push
any changes to GitHub you can just type `git push`.


    Keep track of all files in a project
    Record any changes to project files
    Restore previous versions of files
    Compare and analyze code
    Merge code from different computers and different team members.



