## Milestone Release

[Assumes Casper is bumped too]

* Update version in Casper README.md 
* Version bump commit "Milestone # version bump"

* Update version in package.json
* Update reference to casper
* Version bump commit "Milestone # version bump & updated Casper reference to match"

* git tag -a #.#.# -m 'Milestone Version #.#.#' on both Casper and Ghost
* git push origin master && git push --tags origin master on both Casper and Ghost

## Database Upgrade Release

* Update version in package.json
* git tag -a #.#.# -m "Patch Version #.#.# - Database upgrade ###-###"
* git push origin master && git push --tags origin master
* merge with build and bump build branch