# Tracking changes

Let's make a new text file called `mars.txt`:
```
$ nano mars.txt
```

In this file, add the line:
```
Cold and dry, but everything is my favorite color
```

Exit and save the file. You can make sure everything saved by opening the file with
```
$ less mars.txt
```

Git has noticed a new file:
```
$ git status
On branch master

Initial commit

Untracked files:
   (use "git add <file>..." to include in what will be committed)

	mars.txt
nothing added to commit but untracked files present (use "git add" to track)
```

`mars.txt` is "untracked", meaning that it is a file in the repository that Git is not yet keeping track of. We tell Git to start keeping track with
```
$ git add mars.txt
```

Running `$ git status` again now shows
```
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   mars.txt
```

Git now knows to keep track of changes to `mars.txt`, but we haven't yet *commited* these changes. Let's run the following command:
```
$ git commit -m "Start notes on Mars"
```

When we run `git commit`, Git takes everything we have told it to track with `git add` and stores a copy permanently inside the special `.git` directory.

The `-m` flag (for “message”) is used to record a short, descriptive, and specific comment that will help us remember later on what we did and why.

Good commit messages start with a brief (<50 characters) statement about the changes made in the commit. More detail can be added by following this summary line with a blank line and additional notes.

Checking the status again, we see
```
$ git status
On branch master
nothing to commit, working directory clean
```

We can see the commit we just made by checking the log
```
$ git log
commit b2d9be95e4bdd162758fe90d7ce08693563b4212 (HEAD -> master)
Author: Samantha Dixon <sam.dixon@berkeley.edu>
Date:   Mon Jul 9 11:25:18 2018 -0700

    Start taking notes on Mars
```

This log will show all of the commits made in reverse-chronological order.

Let's make more changes to the file. Using your favorite text editor, add another line to `mars.txt`. Running `git status` again, we see that Git has noticed the modification.
```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   mars.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

We can check the difference between the version last commited and the current version with
```
$ git diff
diff --git a/mars.txt b/mars.txt
index df0654a..4826d23 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,2 @@
 Cold and dry, but everything is my favorite color
+More notes...
```

Let's commit this new change:
```
$ git add mars.txt
$ git commit -m "Add more information about Mars"
```

Note that we have to `add` the Mars file before we make the commit. This is so that you can break your changes up into logical pieces, rather than commiting all changes at once. Think of `git add` as placing changes in a staging area, while `git commit` permanently records this staging area.

# Let's practice

We'll spend a few minutes staging and committing changes to our new repository. Try new things like:

* Adding new subdirectories
* Committing many files at once

[Putting it on GitHub](github.md)