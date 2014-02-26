Contents of this page:

* [Quick Summary](#quick-summary)
* [Notes on writing good commit messages](#Notes-on-writing-good-commit-messages)
* [Submitting Pull Requests](#submitting-pull-requests)
* [Working with issues](#working-with-issues)
* [Branching Strategy](#branching-strategy)
* [Release Procedure](#release-procedure)
* [Database Changes](#database-changes)
* [Navigating GitHub](#navigating-github)

Full details
[Forking Workflow](http://www.atlassian.com/git/workflows#!workflow-forking)

Other interesting reading:
* [GitHub Patterns](http://blog.quickpeople.co.uk/2013/07/10/useful-github-patterns/)
* [Git Workflow](https://sandofsky.com/blog/git-workflow.html)

## Quick Summary

Each developer should fork the private core Ghost repo into a private repo of their own and clone this as their local repo. Remember to add the main repo as a remote:

    git remote add upstream git@github.com:TryGhost/Ghost.git

The main repository's master branch always contains the latest changes. For more info on branches, see the [branching strategy](#branching-strategy) notes.

Changes should adhere to our [coding standards](Code-standards), commit messages should follow our [notes below](#notes-on-writing-good-commit-messages), and pull requests should be submitted as per the [guidelines](#submitting-pull-requests)

## Notes on writing good commit messages
##### Commit Messages
* The first line of your commit message should be a short (80 chars) public description of what you have achieved with the commit. This is what appears in the change log. 
* Leave a blank line after the first line
* The 3rd line should reference the issue with `issue #000` if you just want to mention an issue or `closes #000` if your commit closes an issue. If you don't have an issue to reference or close, think carefully about whether you need to [raise one](https://github.com/TryGhost/Ghost/blob/master/CONTRIBUTING.md#raising-issues) before opening a PR.
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

The easier it is for us to merge a PR, the faster we'll be able to do it. Please take steps to make merging easy and keep the history clean and useful.

**always work on a branch**, it will make your life much easier - honest. Not touching the master branch will also simplify keeping your fork up-to-date.

**use issues properly**, we have a whole set of [guidelines on how to raise an issue](https://github.com/TryGhost/Ghost/blob/master/CONTRIBUTING.md#raising-issues). Bugs, changes and features are all different and should be treated differently. Use your commit message to close or reference issues. The more information you provide, the more likely it is your PR will get merged.

*Note:* If you are not comfortable with git & using rebase, make a special 'merge' branch of your branch to do these things on, then if something goes awry you can always go back to your working branch and try again.

#### Clean-up history

Whilst you're working on your branch on your own, you can do all the commits you like - lots of little commits are highly recommended. However, when you come to submit a PR, you should clean your history ready for public consumption.

- Run `git log master..your-branch-name` to see how many commits there are on your branch
- Run `git rebase -i HEAD~#` where # is the number of commits you have done on your branch

Use the interactive rebase to edit your history. Unless you have good reason to keep more than one commit, I recommend marking the first commit with 'r' and the others with 's'. This lets you keep the first commit only, but change the message. Your commit message(s) should follow the pattern described in the [notes](#notes-on-writing-good-commit-messages) above. The first line of your commit message will appear in the change log which goes out to our VIPs with each pre-release, so please keep that in mind.

#### Check it passes the tests

Run `grunt validate` to check that your work passes JSLint and the server-side mocha unit tests. If this fails, your PR will throw an error when submitted.

Our functional tests are not yet hooked up to grunt validate, but details on how to run them can be found in `core/test/functional/base.js` if you're making changes to the UI it's worth running these.

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

### What Happens Next

Firstly, we will give your code a read through. Small changes usually get merged as soon as we've had chance to read through them. For more involved changes one of us will checkout your PR, rebase with master if required and then run basic sanity / regression tests on the code, run the casper tests and re-run grunt validate. If your PR has fallen behind master and can no longer be merged, we will in most cases rebase / merge master. In some cases with lots of small changes we will ask you to do this as you are more familiar with your changes than we will be.

## Working with issues

Feel free to pick up any issue which is not assigned. Please leave a comment on the issue to say you wish to pick it up, and it will get assigned to you.

## Branching Strategy

`master` on the main repository always contains the latest changes. This means that it is WIP for the next minor version and should NOT be considered stable.

Stable versions are tagged using [semantic versioning](http://semver.org/). 

Along with the master branch, there is always a branch open for bug fixes that might need to go into a patch release. For example if the current released version is 0.3.3, you'll find a branch called 0.3-maintenance.

There may be several patch releases in between minor versions. A patch release does not contain master, it contains the previous release + specific fixes that may have been applied directly, or cherry-picked from master.

On your local repository, you should always work on a branch to make keeping up-to-date and submitting pull requests easier, but in most cases you should submit your pull requests to `master`. Where necessary, for example if multiple people are contributing on a large feature, or if a feature requires a database change, we make use of feature branches. If you are working on something which you feel needs to go into a feature branch, let Hannah know and she will create this for you.

## Release Procedure

The [roadmap](Roadmap) outlines the basic features that we want to get into a minor version release (i.e. 0.4, 0.5, 0.6).

Each release has an associated milestone in GitHub, against which issues are assigned. There are usually issues for each milestone feature, plus other bug fixes and enhancements that we would like to get done.

Each Milestone has a due date. This date is usually a Monday, for example for 0.5 this is Monday 31st March. The due date is the last day on which PRs can be submitted for the milestone. Once we get to the end of the due date, any new PRs will not be considered.

The following Tuesday and Wednesday will be used to merge all PRs which made it into the release and are ready, and for testing the whole package.

On the Thursday, the release candidate .zip will be generated and made available. We will ask that it be tested by as many people as possible! There will be 4 days (inc weekend) for testing. 

Finally, on the following Tuesday, if all has gone well, we will provide the release zip as the new download on Ghost.org, and add it to the releases on GitHub. 

## Database Changes

Database changes require quite a bit of work around migration, exports and imports. As it stands, we currently always deliver database changes along with a minor version bump. Therefore it is important that all database changes are made on a branch so that they can be merged at a time when version bumping is convenient.

## Navigating GitHub

Ghost's GitHub is full of useful information if you know how to find it, this page is a quick guide to the conventions and hidden stuff you'll find.

### Branches

In addition to the [Branching Strategy](#branching-strategy) documented above, you may find the following branches:

**gh-pages** - this branch contains all of the code and content for http://docs.ghost.org. This is open to contributions.

**###-data-updates** - a branch starting with 3 numbers is probably to do with schema changes that require us to bump the database version number.

**ember** - a branch we're currently using to rewrite our admin UI in ember

### Open Issues

Open issues on GitHub are a combination of things we're actively working on, or will be working on soon and bugs. Our [contributing guidelines](https://github.com/TryGhost/Ghost/blob/master/CONTRIBUTING.md) contain lots of information about raising an issue. 

Some issues start with [Discussion] which means there is no active work to be done, we're just deciding what to do or how to do something.

Others start with [Draft] indicating the issue is a placeholder for some work we know we need to do, but we aren't 100% sure what it looks like yet.

You may also see [Investigation] which is our equivalent of a spike, it usually means that the work to be done does not require a PR, but rather some testing or learning around how a particular approach might solve a problem.

### Pull Requests

Pull requests (PRs) for Ghost tend to fall into four loose categories:

1) Works in progress - something that is partly finished, or may have a problem and hasn't been worked on in a while. These are marked with [WIP].
2) PRs marked [Docs] are PRs to the `gh-pages` branch which include general updates / fixes to docs.ghost.org
3) [Translations :/??] indicates that this is a pr to the gh-pages branch which contains translations for a given language, these are often long-lived PRs
4) Everything else is a standard PR waiting to be merged.

There is a Chrome Extension available that will filter the PRs into those Groups, which is useful if you find the docs PRs clutter your view: https://github.com/ErisDS/ghost-github-chrome-extension *note:* it doesn't work very well when there are a LOT of PRs :( but it's open source! So please feel free to fix it :)

PRs generally get assigned to either @erisds or @sebgie, this indicates who will test the PR and make sure it is ready to be merged.

### Milestones

The [milestones](https://github.com/TryGhost/Ghost/issues/milestones) page in GitHub lists out all the milestones with open issues against them, in order of delivery date. Ghost milestones are usually tied to minor version releases for Ghost, such as 0.5 or 0.6 which means the milestone page closely mirrors our [Roadmap](https://github.com/TryGhost/Ghost/wiki/Roadmap). 

![milestones](http://puu.sh/7bzhv.png)

Sometimes we also run side projects which have a milestone to keep all the issues together, such as the current [Ember.js](https://github.com/TryGhost/Ghost/issues?milestone=17&state=open) project.



<img alt="labels" src="http://puu.sh/7bBlE.png" align="left" />

### Labels

Ghost tries to use labels to indicate what aspect of the code base an issue belongs to, and we try to avoid workflow labels. We do have a `[TOP PRIORITY]` label that is used to indicate when an issue is required to close a milestone, and a `[QA]` label to tell QA engineers about any issues which require particular testing attention.

`[epic]` issues are intended for managing groups of issues. The are not a unit of work, but rather used for managing smaller projects within a milestone.

We also have a special label `[beginner]` which is used to indicate that an issue may be good for people who are new to the Ghost code base (as opposed to new to development), this is to help new contributors get their first commit :)

The `[client]` and `[server]` labels are intended to show which 'side' of the code base an issue belongs, with client issues referring to the ember app, and server issues referring to serving blogs, or core functions like middleware.

The `[api]` label refers to the JSON data api

The `[data]` label refers to anything in the models or schema - the data layer underneath the api.

The `[ghost-ui]` label is a place holder marking issues that may be moved to or solved by development on the [Ghost UI](https://github.com/TryGhost/Ghost-UI) framework.

`[importer]` is a project-specific label intended for the 0.5 milestone only

All the other labels should be self-explanatory.


