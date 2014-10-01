## Submitting an Issue

Steps to perform before submitting an issue:

* Confirm source of issue is from Ghost core and not caused by a plugin or theme
* Confirm you are running the latest version of Ghost
    * do a git pull --all (or use the [Ghost pull script](Git-pull-script) to see exactly what changed in your pull)
* [Search the issue queue first](https://github.com/TryGhost/Ghost/issues?state=open)

When raising an issue, please follow the [contributing guide](https://github.com/TryGhost/Ghost/blob/master/CONTRIBUTING.md#reporting-an-issue), which also has a template that you can use & a link which will automatically create an issue with the barebones template.

## Checkout GitHub Pull Request Locally

If you need to test a PR, see this handy guide on the dev blog: http://dev.ghost.org/easy-git-pr-test/

## git pull script

I (Andy Boutte) use this script instead of a `git pull --all` mainly so that it will generate the github compare URL for me.  Once the github compare url is generated I open that up and see if any of the commits are big issues that are worth taking a look at.

```
#!/bin/bash

#move into the right ghost directory
cd /var/www/master.ghost

#git commit hash of most current commit pre pull
prepullhash=`git rev-parse --verify HEAD | awk '{print substr($0,1,7)}'`

#close all screen sessions
screen -S master -X quit
#screen -S weekly -X quit
#screen -S nightly -X quit

#stash all changed files (ie config.js I have modified but I want to make sure I get the most up to date version)
git stash

#pull changes from github
git pull --all

#git commit hash of most current commit post pull
postpullhash=`git rev-parse --verify HEAD | awk '{print substr($0,1,7)}'`

#run upgrades
npm install
sleep 2
git submodule update
sleep 2
grunt
sleep 2
grunt init
sleep 2

#start new screen sessions for each site
screen -S master -d -m npm start

#echo out some empty lines so I can see compare URL
printf "\n\n\n\n"

#generate GitHub Compare URL
compareurl="https://github.com/TryGhost/Ghost/compare/$prepullhash...$postpullhash"
echo $compareurl

#echo out some empty lines so I can see compare URL
printf "\n\n\n\n"
```