I use this script instead of a `git pull --all` mainly so that it will generate the github compare URL for me.  One the github compare url is generated I open that up and see if any of the commits are big issues that are worth taking a look at.

`
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
`