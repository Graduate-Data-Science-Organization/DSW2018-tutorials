# Create a new repository

Let's create a new directory to work in and navigate to that directory:
```
$ cd ~/Desktop
$ mkdir planets
$ cd planets
```

Within the directory `planets`, we'll be making a new directory to track changes

```
$ git init
```

Now, by running `$ ls -a`, we should see a new subdirectory `.git`. `.git` is where all of the history and metadata for the `planets` project is stored. Deleting `.git` deletes this history.

We can see the status of our new repo with
```
$ git status
```
which returns something like
```
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

[Start tracking changes](track_changes.md)