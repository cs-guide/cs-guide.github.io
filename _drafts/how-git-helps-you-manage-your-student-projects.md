
As a student you probably have some way to organize your projects and files on your computer.
These may include assignments, personal projects, resumes and others.
Especially for larger and important projects you most likely create backups of your work.
If not, you will probably regret it at some point :)

I used to send backups to my email or save them on a USB stick. 
However, the problem with these types of backups is that they take quite some time if
you have to create them manually. As your project grows, this process will take even longer.

Because humans are lazy, you will simply skip or forget about backing up your files. 
It could also happen that you accidentally delete or edit files that you didn't mean to edit.
In case something goes wrong, these simple mistakes might cost you hours or even days of work.

You might also have local backups, creating a folder for each new version.
This could quickly lead to a nightmare like this:

![Image](/assets/img/test.PNG)

Also, what if you wanted to cooperate with someone else on your project?
If each of you would work on a different section of the project, collaboration could be pretty
stressful. In order to share updates with each other, you would have to send
new versions of the project via email or use a sevice like Dropbox or Google Drive.
But this way you will never have a complete picture of the current state of the project,
since files are scattered everywhere on different computers.

I could go on for ever about these issues but it's time to focus on a solution.

# What is Git?

By now, you should have a basic understanding of what the most common problems are that
can occur when working on a project that involves multiple files, versions or people.

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



