Purrfect
========

A demo repo for the greatest cat website ever created during a lab on git.

# Demo Walkthrough

Click on the link it the talk.
    Go to this URL:
    https://github.com/michaelsergio/purrfect

You should be logged into GitHub.
Your account name should be in the top right-hand corner.
Click fork. 

If you click on your user name you should see your account dashboard.
Click on repositories. 
These are all your repositories including the forked copy of my project.

Find the HTTPS clone URL on the right side of the page. Copy it.

Type git clone and paste the url you have.
    git clone https://github.com/yourname/purrfect.git

You now have a local working copy.

If you go back to the git page for the project you'll notice theres one open
issue.

The first thing well do is make a feature branch to develop on.

To see all branches
    git branch 
Make a branch
    git branch better-cat

The star is the branch you're currently working on.

To switch to better cat do
    git checkout better-cat

SHORTCUT: To create a branch and switch to it use:
          git checkout -b better-cat

If you do git branch again you should see the star on better-cat.

Now go download a cat from the internet (don't take too long).
Add it to the imgs folder.
Change the url in index.html to the correct filename (remember the imgs/).
Open the index.html file in a browser and confirm you cat image is still there.

Now do:
    git status

You should see your file as untracked.
Read the output, it says the thing you most likely want to do.

To track the file, or to add it to the staging area, we do:
    git add imgs/<YOUR_CATFILE_NAME>

Do git status and you'll see it is moved from "Changes not staged for commit"
to untracked files.

  If you do a "git diff" now you'll the difference between whats in you working
  directory and whats in staging.

Add your html to staging.
    git add index.html

If you do a git status now, you'll see both files in changes to be committed.
(Notice: if you read the output, it tells you how to unstage a file if you added
 something by accident)

Now we commit the changes to our local repository.
    git commit 

An editor will open up. Type your commit message here.
It should be descriptive saying what you did, because everyone will see it!
Because our project is hosted on GitHub in your commit message reference the
issue by typing #NUMBER with no space.

If your using nano press ^X (thats Control X) to exit and save your file.
If you don't save your file, the commit will not happen.

SHORTCUT: To type a message without an editor do:
          git commit -m "YOUR MESSSAGE HERE"

TIP: If you made a mistake do "git commit --amend" to retype the last message.
     DO NOT do this if youve already pushed to another repo.

Now a git status will show that your working directory is clean and all your
changes are tracked in your branch.

If you do "gitk" you'll see your current projects graph.
You will see better-cat on top of master.

Now that the feature is complete, do a 
    git checkout master

If your reload index.html in your browser you'll notice its still in the
previous state.

Lets merge the changes we made in the better-cat branch.
    git merge better-cat

There should be no merge conflicts yet.

If we look at our log we see the changes have been made.
    git log  
    (q to quit)
and of course we can reload our page to see the changes.

See we no longer need our feature branch we can delete it.
    git branch -d better-cat

NOTE: If there we're unmerged changes on our branch we would need to use the 
      destructive delete -D flag instead. Git doesn't like to be destructive so
      it warns us if we try to do this.

If we look at "git log", we notice every commit has a SHA1 hash next to it.
Say we wanted to look difference between the current and the previous commit.
We could do:
     git diff <THE_OLDER_COMMITS_HASH>
     (q to quit)

NOTE: We don't need to type out the entire hash, usually 6 is unique 
      enough to figure out the rest.
NOTE: The top commit is referred to as HEAD.


Now we want to push our changes back to our personal public repo.

To see what servers we know about do:
     git remote

By convention, our main upstream repo is called "origin".
If you do "git remote show origin", you'll see exactly what origin refers to.

Lets push our local repo back to out public one.

Do:
   git push origin master
This means push our current branch to the REMOTE named origin on the 
BRANCH master.
NOTICE: In this case, it is a coincidence our local branch is named master.
        We could have pushed the better-cat branch directly to master using the
        same command, but that would be confusing so we don't do. This would be
        useful if you wanted to have a better name on the remote that what your
        current branch was named.

If you go to git you should notice you have the updated files.

If you go to michaelsergio/purrfect issues, you should notice by using #1 in
github that your issue is referenced in the issue manager.

See slide at this point.


Now on your page, submit a pull request.
It shows a diff of what your doing.
Create a pull request and leave a good comment explaining what you did.
Also use the issue number (#2) to refer to the issue your fixing.

I will merge one users commit and that will close the commit.

I'm going to leave my cat and add the new cat.
This will leave everyone with a merge conflict.

If you go to your forked git repo, you should notice a message saying that it is
off by a few commits. Lets get you up to date.

To do this we need to added the primary repo as a remote we can pull from.
To do this:
    git remote add primary <GIT_URL_FROM_MICHAEL_SERGIO_BRANCH>

If you do git remote, you should see primary on the list.

On your master branch, do:
    git pull primary master

A merge conflict should be presented. We need to fix it.
index.html should be a unmerged path.
Lets open that in an editor.

We should see the arrows <<<<<<< ====== >>>>>>>
Here we should correct the conflict.
Lets keep all three cats. Delete the arrows.
The file should look correct now.
Save and quit the file.

Use "git add index.html"  to stage the changes.

Tip: git add works on directories as well as files. You can add multiple files
     at one like this. Remember in Unix "." is the current directory.

Do git commit to commit to your local repository.
Do git push to push to your forked copy.




## Reverting a commit.
Make sure your branch is clean. ("git status" should come up with nothing)
Change a file and commit the change.
Look at git log and determine the hash of the commit before the change you just
made.

You can go back to an old commit by doing:
    git checkout <OLD_COMMIT_HASH>

To go back to the most recent commit do:
   git checkout master


If you dont like the changes made by the HEAD commit try
   git revert HEAD

If you look at the log, you'll see the changes were both made and recorded and
the repo is in the original state.
