# git update
Update a branch with new updates based on Ghost Git Workflow.

## Download
[http://cl.ly/Plja](http://cl.ly/Plja)


## Install
* Unzip `git-update.zip` 
* Open up git-update directory
* Run `sh git-update-install.sh` from terminal.


## Usage
Ref: `git update --help`

### Synopsis
`git update [-m|--master <branch-name>] [-b|--branch <branch-name>]`


### OPTIONS

`--master` Sets the target branch to retrieve  updates  from.  Defaults  to `master`.

`--branch` Sets  the target branch to apply and rebase updates to. Defaults to the current branch.

`--help` Display `man git-update` pages.


### EXAMPLES

`git update`: Updates current branch with master updates

`git update -m  different-base-branch  -b  new-branch`: Update  `new-branch` with updates from `different-base-branch`