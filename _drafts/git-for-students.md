
Have you heard about Git before but didn't quite know what's so special about it?
Or maybe you thought git would be a useful tool to know but didn't really have the motivation to get started?

Either way, after reading this article you will hopefully have a better understanding
of why you should learn git and how to apply it to your own projects.

## Motivation

The following example demonstrates a possible scenario in which git
would reduce a lot of issues if it were used. Of course, there are
many other areas apart from software development where git can and should be used. More on this later. 

> Ben is a mobile developer and decides to create a new Android game.
He starts right away and a few hours later a basic prototype is ready that 
he wants to share with his friends.  
For a lack of a better alternative, he sends them an email and attaches the
project as a zip file. One of his friends, Devan, loves the
idea and wants to help him by creating better graphics for the game.<br><br>
He draws some nice images and sends them back to Ben. In general, Ben finds them great but nonetheless
asks Devan to tweak them a little bit. He does as he was told, and sends Ben the updated version of the game.
Ben is eager to try out the new graphics and starts up the app for a test.  
Right after he starts the app, it crashes. As he looks into it, he notices that an important script file is missing
that contains some of his code.

There are a few things you might have noticed in the workflow described in this example.
Firstly, sending the project back and forth between developers via email doesn't seem like
a particularly good idea. As the project grows, this will become an increasingly slower process. 

Secondly, notice how Devan could delete source files that were completely unrelated to the part
he was currently working on. In fact, Ben didn't even notice that a file was missing at first.

Also, when Ben asks Devan to change some of the images, he has to send the whole project back
even though he only worked on a small section of the project.

This also leads to another problem: Each time a new version of the game is ready (either a minor
version change like a bugfix, or a major change that adds a new feature)
a new project folder for that version has to be created. This might lead to a nightmare like this:

[IMAGE]

Why is this so bad? Well, several things: One obvious reason is that the disk space usage
will increase with every new version and may soon become unbearable.
The more important issue, however, is the fact that it makes reverting back to a previous
state of your project hard. In order to be able to undo a change, you would have to create a
new version beforehand. Otherwise you could not be sure that your changes won't be lost
in case you mess something up.
Even if you create regular backups, say, multiple times a day, that would not be a
particularly precise reverting mechanism.

This is where Git comes into play.


## What is Git?

Git is a version control system. This means that it can be used to track changes in the source
files of a software project. However, it is not limited to software but can be applied to 
virtually any project that involves multiple files. For example, a writer might use git to
manage different chapters in a book.

Git makes collaboration easy through branches. Each developer can work on his own separate
version of the project which makes it harder to break things accidentally as seen in the example.
People can create and upload changes they make to a central repository instead of having
to manage dozens of scattered files. 

Since Git tracks any changes in the files that you add/delete or edit, it allows you to
easily go back to a previous state. This frees you from having to manage multiple versions yourself
as local backups.


## What is GitHub?

GitHub ≠ Git! GitHub is a website that allows you to store and showcase your projects.
It relies on Git to ... 


## Getting started with Git






- additional resources
git book

