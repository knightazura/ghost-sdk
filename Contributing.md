Welcome to the Ghost repository!

This document is intended as a one-stop shop for getting started with contributing to the codebase. Please feel free to add anything you find to be missing.

## Getting Started with the Codebase

You first port of call should probably be the [working on ghost core](https://github.com/TryGhost/Ghost/blob/master/CONTRIBUTING.md#working-on-ghost-core) guide in the CONTRIBUTING.md which details all the dependencies you need to build Ghost from the repo.

## Code Standards

All code should conform, strictly, to the Ghost project [Code Standards](https://github.com/TryGhost/Ghost/wiki/Code-standards).

All HTML and CSS should conform to the [Code Guide](http://github.com/mdo/code-guide), maintained by [Mark Otto](http://github.com/mdo).

All code must also pass our unit and functional tests. You can check this by running `grunt validate`. We use Travis CI to run both a linter and our unit tests against all Pull Requests.

## Getting Stuck In

Work is very much underway towards achieving version 0.3. You can find out the plan by reading the [Version 0.3 Roadmap](https://github.com/TryGhost/Ghost/wiki/Roadmap#version-03---kickstarter-access---est-16th-september) and also take a look at the [issue list](https://github.com/TryGhost/Ghost/issues?milestone=2&state=open). If you see any issue you are interested in working on, let Hannah know by leaving a comment or dropping her a message in IRC/Skype.

If you have ideas for something you'd like to implement or improve which isn't on the roadmap, feel free to open issues and PRs for these. Opening a PR or Gist for a refactor or idea for something is often the best way to get a discussion started.

## Submitting Changes

Please read the [Git workflow](https://github.com/TryGhost/Ghost/wiki/Git-workflow) documentation with regards to writing commit messages, opening Pull Requests, branching strategies and other general git process related stuff.

When submitting Pull Requests or Issues, often screenshots or .gifs of the problem or new functionality can be beneficial. We recommend [LICEcap](http://www.cockos.com/licecap/) as a tool to record .gifs of your screen (set your 'FPS' to '24' to get smooth results).