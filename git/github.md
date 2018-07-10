# Sharing a Repository on GitHub

GitHub is a popular place to host repositories so that many people can work on it collaboratively. Other popular services include BitBucket and GitLab.

Before arriving, you should have created a GitHub account. Log into that account now and create a new repository by clicking the "+" in the upper right.

Name the repository 'planets' and add a description if you'd like. Click the green "Create repository" button and move to the next screen.

Filling out this form effectively runs the following commands on the GitHub servers:
```
$ mkdir planets
$ cd planets
$ git init
```

You now have two separate `planet.git` repositories: one on your local machine and another on the GitHub server. The GitHub repository is not yet connected to your local repository, so we'll remedy that now.

After creating a new repo on GitHub, we are led to a screen that allows us to copy a link to the GitHub repo. Copy this link and run in the terminal:
```
$ git remote add origin https://github.com/sam-dixon/planets.git
```

`origin` is the nickname for our local repository. To send the changes on your local repository to the remote repository, run
```
$ git push origin master
```

In the future, you can pull changes from the remote repo to your local repo with
```
$ git pull origin master
```
Running this command now won't do anything, since we synchronized our local repo with the remote repo with `git push`. However, if someone else made changes to the remote repo, you can have those changes reflected in your local repo by running this command.

[More about collaborating on GitHub](collaborate.md)