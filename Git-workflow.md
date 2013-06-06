Full details
[Forking Workflow](http://www.atlassian.com/git/workflows#!workflow-forking)

**Please note:** I will always try to merge your pull request, or at least give a reason why your pull request has not been merged, within 24 hours at the absolute latest.

## Quick Summary

Each developer should fork the private core Ghost repo into a private repo of their own and clone this as their local repo. Remember to add the main repo as a remote:

    git remote add upstream git@github.com:TryGhost/Ghost.git

Once a change is ready to be added back to the core repo, a pull request should be issued. For the immediate future only, all pull requests will be handled by Hannah Wolfe.

Be sure to pull from the core repo regularly :)

## Submitting Pull Requests

The easier it is for me to merge a PR, the faster I'll be able to do it. Please take steps to make merging easy and keep the history clean and useful.

Firstly, **always work on a branch**, it will make your life much easier - honest. Not touching the master branch will also simplify keeping your fork up-to-date.

*Note:* If you are not confortable with git & using rebase, make a special 'merge' branch of your branch to do these things on, then if something goes awry you can always go back to your working branch and try again.

#### Clean-up history

Whilst you're working on your branch on your own, you can do all the commits you like - lots of little ones are recommended. However, when you come to submit a PR, you should clean your history ready for public consumption.

- Run `git log master..your-branch-name` to see how many commits there are on your branch
- Run `git rebase -i HEAD~#` where # is the number of commits you have done on your branch

Use the interactive rebase to edit your history. Unless you have good reason to keep more than one commit, I recommend marking the first commit with 'r' and the others with 's'. This lets you keep the first commit only, but change the message.

#### Write meaningful commit messages

Write a useful commit message. Unless your change is very very small, your commit message should have a summary line, a blank line, and then more details. E.g.

```
Fixing bug in registration

Switching over to abstracted data provider meant that email_address
accidentally got passed to the model as email and therefore could not
be found. This is now resolved.
Also, added trailing slash to register route, which I believe should be there
```

#### Submit!

Now that your history is nice and clean, fetch the latest updates from upstream. Assuming you never touched the master branch, do:

    > git checkout master
    > git pull upstream master

Then rebase your branch/changes on top of master:

    > git checkout my-branch-name
    > git rebase master

And finally push your work to your fork:

    > git push -u origin my-branch-name

GitHub will offer to create a pull-request from newly created branches automatically.

Now submit your PR with all the latest changes from master and a nice clean history with useful commit messages. Finish up by adding a description to the PR which details any interesting changes, any tools or libraries you've added and warnings for any breaking changes.

### Updating a Pull Request

If your PR has fallen behind and can't be merge cleanly, just re-do the steps above (pull from master, rebase your branch), then force push to your branch using `git push -f origin my-feature-branch`. This will update the PR commits. Of course, never force push to any branch you have shared with others.

Thanks!

*Note:* - this is my way of getting everything neat and tidy, you may have another, as long as the result is nice easy-to-merge PRs.

### What I do:

I will read through your code, checkout your PR, merge master if it's out of date and run basic sanity / regression tests on the code & re-run grunt validate if needed. If you haven't followed the above steps, I will do my best to achieve the same results. If you have, I can just press the nice green button on github.


## Working with issues

Feel free to pick up any issue which is not assigned. Please leave a comment on the issue to say you wish to pick it up, and it will get assigned to you.