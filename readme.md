
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
### add

```

git clone

```

```
git add <filename>
git add *

```

### commit
When you commit, git creates a new commit object using the files from the stage and sets the parent to the current commit.
It then points the current branch to this new commit.
```

git commit -m "commit"

```

### remote
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

### checkout
The checkout command is used to copy files from the history (or stage) to the working directory, and to optionally switch branches.

When a filename (and/or -p) is given, git copies those files from the given commit to the stage and the working directory. For example, git checkout HEAD~ foo.c copies the file foo.c from the commit called HEAD~ (the parent of the current commit) to the working directory, and also stages it. (If no commit name is given, files are copied from the stage.) Note that the current branch is not changed
```
git checkout HEAD~ files
```

When a filename is not given but the reference is a (local) branch, HEAD is moved to that branch (that is, we "switch to" that branch), and then the stage and working directory are set to match the contents of that commit. Any file that exists in the new commit (a47c3 below) is copied; any file that exists in the old commit (ed489) but not in the new one is deleted; and any file that exists in neither is ignored.

```
git checkout <branchname>
```
When a filename is not given and the reference is not a (local) branch — say, it is a tag, a remote branch, a SHA-1 ID, or something like master~3 — we get an anonymous branch, called a detached HEAD. This is useful for jumping around the history. Say you want to compile version 1.6.6.1 of git. You can git checkout v1.6.6.1 (which is a tag, not a branch), compile, install, and then switch back to another branch, say git checkout master. However, committing works slightly differently with a detached HEAD;

```
git checkout master~3
```

Committing with a Detached HEAD

When HEAD is detached, commits work like normal, except no named branch gets updated. (You can think of this as an anonymous branch.)

Once you check out something else, say master, the commit is (presumably) no longer referenced by anything else, and gets lost
```
git checkout master
```
If, on the other hand, you want to save this state, you can create a new named branch using git checkout -b name.

```
git checkout -b name
```

### reset
The reset command moves the current branch to another position, and optionally updates the stage and the working directory. It also is used to copy files from the history to the stage without touching the working directory.

If a commit is given with no filenames, the current branch is moved to that commit, and then the stage is updated to match this commit. If --hard is given, the working directory is also updated. If --soft is given, neither is updated.
```
git reset HEAD~3
```

If a commit is not given, it defaults to HEAD. In this case, the branch is not moved, but the stage (and optionally the working directory, if --hard is given) are reset to the contents of the last commit.
```
git reset
```
If a filename (and/or -p) is given, then the command works similarly to checkout with a filename, except only the stage (and not the working directory) is updated. (You may also specify the commit from which to take files, rather than HEAD.)
```
git reset -- files
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
A merge creates a new commit that incorporates changes from other commits. Before merging, the stage must match the current commit. The trivial case is if the other commit is an ancestor of the current commit, in which case nothing is done. The next most simple is if the current commit is an ancestor of the other commit. This results in a fast-forward merge. The reference is simply moved, and then the new commit is checked out.

### diff

```
#show difference between stage and working dir
git diff

#show difference between HEAD and working dir
git diff HEAD

#show difference between b325c and da985
git diff b325c da985
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
