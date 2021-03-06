# Contributing

----RMP-----
[1-3 same as the flow we're used to, you'll only have to do these once]
1. Fork the official remote repo 
    (in Github in your browser)

2. Clone your new repo to your computer 
    git clone http://rmpardee/centillionplus greenfield

3. Add the official repo as an upstream so you can pull from it later
    git remote add upstream http://centillionplus/centillionplus


[4-7 we'll be repeating with each feature]
4. Make a new branch to work on whatever you're working on. Don't work directly on master
    git checkout master
    --> make sure you start on the master branch so that your new branch is based on that and not on a different branch
    
    git checkout -b myFeatureBranch
    --> this creates the new branch called myFeatureBranch and the -b then moves you to that new branch.

    [likely some time will pass here while you're working on this feature. You will be making frequent commits and push to the same branch on your origin remote repo with git push origin myFeatureBranch]

5. When you're ready to deploy the feature, make sure your master branch is up-to-date with the official repo's master branch, before pushing up to your origin myFeatureBranch
    git checkout myFeatureBranch
    --> make sure you're on your feature branch first

    git pull --rebase upstream master
    --> rebase the branch you're on onto whatever is on the upstream's master branch (the changes other team members have made since the last time you did this)

    --- If merge conflicts emerge will rebasing:
    a) In the file where the conflict is, you'll see both conflicting versions. Change the file to exactly how you want it (removing all >>> etc that were added), and save.
    b) Back in your CL, git add that file (but do not do a commit! This is the point of rebasing, to avoid merge commits)
    c) run 'git rebase --continue' to move on to the next merge conflict (if any), and repeat until completed.

6. On GitHub's site in your browser, submit a pull request from your origin remote repo's feature branch to the official repo's master branch.
--> Other team members should review any pull requests and be merging them in. You should NOT merge your own pull requests, you should only merge other team members'.

7. Once your feature's been merged by someone else (or another teammate has a PR that gets merged in), back in your local repo, go to your master branch and update it with what's currently on the upstream's master.
    git checkout master

    git pull upstream master
    --> (for some reason adding --rebase here seems to make it not work, so just do a regular pull)
    --> Your master should now match the official repo's master. 

    git push origin master
    --> Bring your origin remote repo's master up-to-date

  You will now repeat #4-7 on your next feature, and the newFeatureBranch will be left behind and not ever updated again.


#### Commit Message Guidelines

- The first line of your commit message should be a brief summary of what the
  commit changes. Aim for about 70 characters max. Remember: This is a summary,
  not a detailed description of everything that changed.
- If you want to explain the commit in more depth, following the first line should
  be a blank line and then a more detailed description of the commit. This can be
  as detailed as you want, so dig into details here and keep the first line short.


### Making a pull request

Make a clear pull request from your fork and branch to the upstream master
branch, detailing exactly what changes you made and what feature this
should add. The clearer your pull request is the faster you can get
your changes incorporated into this repo.

Put a message in our Slack channel once you've done the pull request. Whoever sees it first should respond on Slack saying they're taking a look. That person will then give your changes a code review, and once they are satisfied they will merge your changes into upstream. **You will never be merging your own pull requests, someone else always will for you.**

If you're reviewing someone else's changes and think it isn't ready to merge, have a conversation with the person who submitted the pull request in our Slack channel. That person can then make more commits to their branch to fix these, then follow this process again from rebasing onwards.

Once it's good to go, merge it, and put a note in Slack again when you've merged. The Scrum Master will adjust the status of the issue on waffle.io.

NOTE: Moving the card on waffle that represents the open PR waiting to be merged to the 'Done' column automatically closes the PR.



