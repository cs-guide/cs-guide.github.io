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
Additionally, the command's options have [changed after Git version 2.0](https://github.com/git/git/blob/master/Documentation/RelNotes/1.8.3.txt#L19-L30). Therefore, I decided to write this article to fully explain all the different options for the add command.
Hopefully this will clear things up!

## What does `git add` do?

```
git add .
```
Stages all files but only in the current directory.

| New files | Modified files | Deleted files |
|-------|--------|---------|
| ✅ | ✅ | ✅ |

![Image](git-add-dot.png)


```
git add ..
```


```
git add -a
```

```
git add -A
```

```
git add -all
```

```
git add *
```

```
git add file.txt
```

```
git add file1.txt file2.txt file3.txt
```

```
git add -u
```

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

