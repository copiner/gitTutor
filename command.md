
Working dir

Index

Repository

```
git --help

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add        Add file contents to the index
   mv         Move or rename a file, a directory, or a symlink
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
   grep       Print lines matching a pattern
   log        Show commit logs
   show       Show various types of objects
   status     Show the working tree status

grow, mark and tweak your common history
   branch     List, create, or delete branches
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   merge      Join two or more development histories together
   rebase     Reapply commits on top of another base tip
   tag        Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
   pull       Fetch from and integrate with another repository or a local branch
   push       Update remote refs along with associated objects


```

```
git init

```

```

git clone

```

```
git add <filename>
git add *

```

```

git commit -m "commit"

```

```
git push origin master

git remote add origin <server>

```

### branch

```
git checkout -b feature

```

```
git checkout master


```

```
git branch -d(delete) feature

```

```
git push origin <bracnch>

```

### update and merge

```
# update

git pull

```

```
#merge <branch> into current branch

git merge <branch>


```

```
git diff
```

### tag
```

git tag 1.0.0 1b2e1d63agh

git log

```


### replace



```

git fetch origin

git reset --hard origin/master

```


```
# basic usage

git add files    

git commit


git reset -- files

git checkout -- files

```
`git add files` copies files (at their current state) to the stage.

`git commit` saves a snapshot of the stage as a commit.

`git reset -- files` unstages files; that is, it copies files from the latest commit to the stage.
Use this command to "undo" a `git add` files.

You can also `git reset` to unstage everything.

`git checkout -- files` copies files from the stage to the working directory. Use this to throw away local changes



It is also to jump over the stage and check out
files directly from the repository or commit
files without staging first

`git commit -a` is equivalent to running git add on all filenames that existed in the latest commit, and then running git commit.

`git commit files` creates a new commit containing the contents of the latest commit, plus a snapshot of files taken from the working directory. Additionally, files are copied to the stage.

`git checkout HEAD -- files` copies files from the latest commit to both the stage and the working directory.



```
[root@wra gitTutor]# git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#       modified:   command.md
#
no changes added to commit (use "git add" and/or "git commit -a")
[root@wra gitTutor]#
[root@wra gitTutor]# git add command.md
[root@wra gitTutor]#
[root@wra gitTutor]# git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       modified:   command.md
#
[root@wra gitTutor]#

````


```

[root@wra gitTutor]# git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       modified:   command.md
#
[root@wra gitTutor]# git reset -- command.md
Unstaged changes after reset:
M       command.md
[root@wra gitTutor]#
[root@wra gitTutor]#
[root@wra gitTutor]# git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#       modified:   command.md
#
no changes added to commit (use "git add" and/or "git commit -a")
[root@wra gitTutor]#

```


```

[root@wra gitTutor]# git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#       modified:   command.md
#
no changes added to commit (use "git add" and/or "git commit -a")
[root@wra gitTutor]# git  add command.md
[root@wra gitTutor]# git commit -m "try"
[master 6dabe41] try
1 file changed, 132 insertions(+), 1 deletion(-)
[root@wra gitTutor]# git status
# On branch master
nothing to commit, working directory clean
[root@wra gitTutor]#

```
