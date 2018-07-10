# What is version control?

Version control is a way to track changes made to a file. The most recent version is just the base document with each change replayed. Reverting to an older version can be done by "undoing" the changes made after that version. Changes made by different collaborators can be combined and incorporated into a single version (as long as there are no conflicts).

Each recorded change made to project files is called a **commit** and the complete history and metadata of these commits form a **repository** (or repo for short).

# Configuring Git
Before diving in, let's make sure Git is up and running on your computer and configure your name and e-mail address.

Git commands on the command line always take the form
`git verb`, where `verb` is what we want to accomplish. You can see a list of available verbs with `git help`.

To configure our Git setup, we'll use `git config`. Type the following commands into the command line, replacing my information with your own.

```
$ git config --global user.name "Sam Dixon"
$ git config --global user.email "sam.dixon@berkeley.edu"
```

**Note**: if you have already signed up for a GitHub account, make sure to use the same email address that you used on GitHub.

[Make a new repo](new_repo.md)