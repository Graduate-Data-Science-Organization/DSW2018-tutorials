# Collaborative Workflow

Find a partner for the next few exercises. One partner will act as the repo owner and the other as a collaborator (we'll switch roles if time permits). Have the owner add the collaborator on GitHub by navigating to Settings>Collaborators and searching for the collaborator's username. The collaborator should receive an invitation to collaborate at [github.com/notifications](https://github.com/notifications).

After accepting the invite, the collaborator needs to get a copy of the remote repo on their local machine. This is known as **cloning** a repo. On the main repo page, copy the remote repository URL and run
```
$ git clone https://github.com/sam-dixon/planets.git ~/Desktop/partner-planets
```

Now the collaborator can make changes to the repository. Add a new file or modify an existing file, then add and commit the changes. Finally, run
```
$ git push origin master
```
to push the new contributions to the remote repository.

The owner can now update their local repo by running
```
$ git pull origin master
``` 

# Branching and Pull Requests

Pull requests are a feature of GitHub that allow collaborators to review and annotate code before changing the master copy of the repository. This is a good practice that
1. Prevents changes from one collaborator from breaking everybody else's repo
2. Allows you to make incremental changes before merging to the main codebase
3. Provides an opportunity to send and receive feedback on your code in order to improve your coding abilities

In order to create a pull request, we first need to create a branch. In the local repository in which you are the collaborator, run
```
$ git checkout -b pr-example
```

If you run `git status`, you'll note that the output should now say `On branch pr-example`. All commits that you make will now be added to this branch, not the main codebase (the `master` branch). Now, once again, modify some of the files in the repository, and add and commit them. Push these changes with
```
$ git push origin pr-example
```

You should see this branch appear on the repo GitHub page. You can also visualize the branch history by clicking "Insights">"Network".

Open a new pull request by clicking the "Pull requests" tab, then New Pull Request. Select the branch `pr-example` from the "compare" dropdown menu. You should see a comparison between the version of the file that is at the head of the `master` branch and the version at the head of the `pr-example` branch. Click "Create pull request", and add more information about what you committed in the text box.

When you submit the pull request, all other repo collaborators can comment on the changes, and suggest improvements. You can even comment on individual lines by going to the "Files changed" tab and hovering over the line you wish to comment on.

When the owner is satisfied with the changes, they can automatically **merge** the branch with the master branch by clicking the "Merge pull request" button on the pull request page. This commits the changes made on the pull request branch to the master branch. You can now delete the pull request branch.

# Managing Conflicts
Automatic merging only works if the changes made to the file are consistent with or independent of each other. If there is a conflict, Git can make us aware of it so it can be rectified.

Let's create a conflict and work through its resolution.

First, make sure that the copy of `mars.txt` that you and your partner have in your respective local repositories are identical. (This should be the case if you've followed the steps so far). Now have one partner make a change to `mars.txt`, add, commit, and push to GitHub.

```
$ nano mars.txt
$ git add mars.txt
$ git commit -m "Setup a conflict"
$ git push origin master
```

Now, the other partner updates the same file, but *without* updating the remote repo on GitHub
```
$ nano mars.txt
$ git add mars.txt
$ git commit -m "Add a conflicting line"
```

If this partner tries to push to GitHub, they should encounter an error. Try it!
```
$ git push origin master
```

Git has found that it can't rectify the two changes. We can work around this by:
1. Pulling the changes from GitHub
2. Manually merge the changes
3. Push the final product to the working branch

First, pull from GitHub:
```
$ git pull origin master
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 3 (delta 1)
Unpacking objects: 100% (3/3), done.
From https://github.com/vlad/planets
 * branch            master     -> FETCH_HEAD
Auto-merging mars.txt
CONFLICT (content): Merge conflict in mars.txt
Automatic merge failed; fix conflicts and then commit the result.
```

Git is warning us about a conflict. Let's look at `mars.txt` in your favorite text editor. You should see some lines that look like this:
```
<<<<<<< HEAD
We added a different line in the other copy
=======
This line added to Wolfman's copy
>>>>>>> dabb4c8c450e8475aee9b14b4383acc99f42af1d
```

The line between `<<<<<<< HEAD` and `=======` is the latest version on the `master` branch, and the line between `=======` and `>>>>>>> dabb4c8c450e8475aee9b14b4383acc99f42af1d` is the conflicting line.

To resolve the merge conflict, edit the file so that it reads the way you wish it to read. Remove the markers (`<<<<<<< HEAD
`, `=======`, `>>>>>>> dabb4c...`) as well.

Now, you can add, commit, and push the changes as usual, and the merge conflict has been resolved.

```
$ git add mars.txt
$ git commit -m "Merge changes to Mars notes"
$ git push origin master
```

Now if the other partner pulls from the remote repository, they should receive the updated (merged) version of the file.

[Wrapping up](resources.md)