Full details
[Forking Workflow](http://www.atlassian.com/git/workflows#!workflow-forking)

Other interesting reading:
* [GitHub Patterns](http://blog.quickpeople.co.uk/2013/07/10/useful-github-patterns/)
* [Git Workflow](https://sandofsky.com/blog/git-workflow.html)

## Quick Summary

Each developer should fork the private core Ghost repo into a private repo of their own and clone this as their local repo. Remember to add the main repo as a remote:

    git remote add upstream git@github.com:TryGhost/Ghost.git

The main repository's master branch always contains the latest changes. For more info on branches, see the [branching strategy]() notes.

Changes should adhere to our [coding standards](https://github.com/TryGhost/Ghost/wiki/Code-standards), commit messages should follow our [notes below](https://github.com/TryGhost/Ghost/wiki/Git-workflow#notes-on-writing-good-commit-messages), and pull requests should be submitted as per the [guidelines](https://github.com/TryGhost/Ghost/wiki/Git-workflow#submitting-pull-requests)


## Notes on writing good commit messages

* The first line of your commit message should be a short (80 chars) public description of what you have achieved with the commit. This is what appears in the change log. 
* Leave a blank line after the first line
* The 3rd line should reference the issue with `issue #000` if you just want to mention an issue or `closes #000` if your commit closes an issue.
* Use bullet points on the following lines to explain what your changes achieve and in particular why you've used your approach

E.g.

```
Show message and don't start on unsupported node versions

closes #292
- added engines and enginestrict properties to package.json
- these provide warnings / errors when installing through npm
- added our own check using this info on start, throws a useful error and stops the app if the node version is not supported
- also switched sqlite3 to the latest version and checked it works with various node versions
```

[See the original](https://github.com/TryGhost/Ghost/commit/6dd753212f1b143f0e6729010ff14b914f1bf576)

## Submitting Pull Requests

The easier it is for me to merge a PR, the faster I'll be able to do it. Please take steps to make merging easy and keep the history clean and useful.

Firstly, **always work on a branch**, it will make your life much easier - honest. Not touching the master branch will also simplify keeping your fork up-to-date.

*Note:* If you are not confortable with git & using rebase, make a special 'merge' branch of your branch to do these things on, then if something goes awry you can always go back to your working branch and try again.

#### Clean-up history

Whilst you're working on your branch on your own, you can do all the commits you like - lots of little commits are highly recommended. However, when you come to submit a PR, you should clean your history ready for public consumption.

- Run `git log master..your-branch-name` to see how many commits there are on your branch
- Run `git rebase -i HEAD~#` where # is the number of commits you have done on your branch

Use the interactive rebase to edit your history. Unless you have good reason to keep more than one commit, I recommend marking the first commit with 'r' and the others with 's'. This lets you keep the first commit only, but change the message. You commit message(s) should follow the pattern described in the [notes](https://github.com/TryGhost/Ghost/wiki/Git-workflow#notes-on-writing-good-commit-messages) above. The first line of your commit message will appear in the change log which goes out to our VIPs with each pre-release, so please keep that in mind.

#### Submit!

Now that your history is nice and clean, fetch the latest updates from upstream. Assuming you haven't changed the master branch, do:

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

If your PR has fallen behind and can't be merge cleanly, just re-do the steps above (pull from master, rebase your branch), then force push to your branch using `git push -f origin my-feature-branch`. This will update the PR commits. Of course, never force push to any branch you have shared with others & be very careful about what you force push.

Thanks!

*Note:* - this is my way of getting everything neat and tidy, you may have another, as long as the result is nice easy-to-merge PRs.

### What I do:

Firstly, I will give your code a read through. Small changes usually get merged as soon as I've had chance to read through them. For more involved changes I will checkout your PR, rebase with master if required and then run basic sanity / regression tests on the code, run the casper tests and re-run grunt validate. If your PR has fallen behind master and can no longer be merged, I will in most cases rebase / merge master myself. In some cases with lots of small changes I will ask you to do this as you are more familiar with your changes than I will be.

## Working with issues

Feel free to pick up any issue which is not assigned. Please leave a comment on the issue to say you wish to pick it up, and it will get assigned to you.

## Branching Strategy

`master` on the main repository always contains the latest changes. Stable versions are tagged using [semantic versioning](http://semver.org/). The main repository also has a `build` branch which is usually a couple of commits behind master and is the branch that our Jenkins server uses to deliver the nightly and weekly builds to VIPs.
On your local repository, you should always work on a branch to make keeping up-to-date and submitting pull requests easier, but in most cases you should submit your pull requests to `master`. Where necessary, for example if multiple people are contributing on a large feature, or if a feature requires a database change, we make use of feature branches. If you are working on something which you feel needs to go into a feature branch, let Hannah know and she will create this for you.

## Database Changes

Database changes require quite a bit of work around migration, exports and imports. As it stands, we currently always deliver database changes along with a version bump. Therefore it is important that all database changes are made on a branch so that they can be merged at a time when version bumping is convenient.