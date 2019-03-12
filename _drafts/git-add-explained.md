:ballot_box_with_check:

If you have used Git before, you definitely came across the `git add` command. If not, check out my 
<a href="{{ site.baseurl }}{% post_url git-github-guide/2019-03-10-git-github-beginners-guide %}">Complete Beginner's Guide to Git</a>.

I noticed that the usage of this command seems to cause a lot of confusion.
Take a look at this article from GitLab for example
([Start using Git on the command line](https://docs.gitlab.com/ee/gitlab-basics/start-using-git.html#add-all-changes-to-commit)):

> To add and commit all local changes in one command:
>
> `git add .`  
> `git commit -m` [...]
>
> Note: The `.` character typically means all in Git.
> {: .notice--primary}

`git add .` does in fact **not** add all local changes! (by the way that is not "one command") There are also several [related answers](https://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add) about this topic scattered on stackoverflow
that only cover the differences between two or three options.
Additionally, the command's options have changed after Git version 2.0. Since the [documentation](https://git-scm.com/docs/git-add) can be pretty hard to read I decided to write this article to fully explain all the different options for the add command.
Hopefully this will clear things up!

## What does `git add` do?

```
git add .
```

| New files | Modified files | Deleted files |
|-----------|----------------|---------------|
| ✅        | ✅             | ✅            |

Stages all files in the current directory and its subdirectories. The `.` refers to the current directory whereas
`..` would refer to the parent directory. If your aim is to stage all files, you should only use this command if
you are currently in the root folder of your project (where your `.git` folder is located). Otherwise, not all 
files might be added. Run `git status` afterwards to confirm that all files have been added.


```
git add <pathspec>...
```

| New files | Modified files | Deleted files |
|-----------|----------------|---------------|
| ✅        | ✅             | ✅            |


[`<pathspec>...`](https://git-scm.com/docs/gitglossary) is used to add one or multiple specific files or folders that match the pattern.
This command gives you precise control about which files will be added.

**Examples:**

| `git add file.txt`            | only adds `file.txt`                                             |
| `git add file1.txt file2.txt` | adds `file1.txt` and `file2.txt`                                 |
| `git add foo`                 | adds all files and subdirectories within the `foo` folder        |
| `git add foo/*.txt`           | adds all `.txt` files within the `foo` folder and subdirectories |


```
git add -A
```

| New files | Modified files | Deleted files |
|-----------|----------------|---------------|
| ✅        | ✅             | ✅            |

Stages all files in the entire working tree unless a `<pathspec>` is specified. You should generally use this option
if you want to make sure that all new, modified and deleted files in your project will be staged. 

**Same as:** `git add --all`, `git add --no-ignore-removal`

**Examples:**

| `git add -A .`            | equivalent to `git add .`                                             |
| `git add -A foo/`         | equivalent to `git add foo/`                                          |

**Note:** This is a change introduced in [Git version 2.0](https://github.com/git/git/blob/master/Documentation/RelNotes/1.8.3.txt#L19-L30). Previously, `git add foo/` used to ignore
removals of files, now it's the same as `git add -A foo/`. This means that the `-A` option is not required anymore when adding a specific folder. Use `git --version` to check your current Git version.
{: .notice--danger}


```
git add *
```

Stages all files except those starting with a dot. This means that for example any `.gitignore` or `.config` files in the directory
would not be added.

```
git add -u <pathspec>
```

| New files | Modified files | Deleted files |
|-----------|----------------|---------------|
| :x:       | ✅   			 | ✅      		 |

Restages files that have been added previously and also removes files from the index that have been deleted.
Use this option if you want to exlude added files that are not in the staging area yet.

**Note:** In previous versions, using this option only included files in the current directory and its subdirectories.
Now `-u` refers to the whole working tree (similar to `-A`). 
{: .notice--danger}

```
git commit -am "A commit message"
```

```
git commit -a
```

```
git add --patch file.txt
```

```
git add -N
```

```
git add -e
```

```
git add -h
```

```
git diff --staged
```
 to check that you staged the correct changes

```
git reset -p
```
to unstage mistakenly added hunks

```
git commit -v
```
to view your commit while you edit the commit message

[Source](https://stackoverflow.com/questions/1085162/commit-only-part-of-a-file-in-git)
https://stackoverflow.com/questions/26042390/git-add-asterisk-vs-git-add-period

## Sources
- [git-scm](https://git-scm.com/docs/git-add) - the official documentation for the `add` command
- [stackoverflow](https://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add/) - difference between `git add -A` and `git add .`

## Further reading
Check out the Pro Git book [online](https://git-scm.com/book/en/v2) or as a [print version](https://www.amazon.com/Pro-Git-Scott-Chacon/dp/1484200772?ie=UTF8&camp=1789&creative=9325&creativeASIN=1430218339&linkCode=as2&tag=git-sfconservancy-20) on Amazon if you want to
learn most of the commands and really understand how Git works behind the scenes.
