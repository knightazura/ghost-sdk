## Initial Setup

### Dependencies

* [NodeJS](http://nodejs.org/) 
* [SCSS](http://sass-lang.com/)
* [Bourbon](http://bourbon.io/)

### Setup Ghost

#### Downloading

To setup up Ghost, the first thing you need to do is download the latest stable version. This can be achieved via the following methods;

* Downloading from [https://github.com/TryGhost/Ghost/archive/master.zip](https://github.com/TryGhost/Ghost/archive/master.zip)

or 

* Using Git, `git clone https://github.com/TryGhost/Ghost.git`

#### Getting Ghost Running

The initial download of Ghost needs some preparation before you can start using it.


* You need to `cd` into your Ghost directory.
* `npm install`
	* If the install fails with errors to do with "node-gyp rebuild", follow the Sqlite3 install instructions
* `grunt init`
* `git submodule update --init`
*  `node app.js`

This should now mean you are running your own local version of Ghost! Woop.

To start using Ghost go to `http://localhost:3333` for the Frontend, or `http://localhost:3333/ghost` for the Ghost Admin.

#### SQLite3 Install Instructions

Ghost depends upon SQLite3, which has to be built for each OS. NPM is as smart as it can be about this, and as long as your machine has all the pre-requisites for compiling/building a C++ program, the npm install still works.

**For Mac users:** The easiest way to do this is to download/install XCode from the App Store (free). This will automatically install all the tools you need - you don't need to open the app.

**For Everyone else:** if you don't have the required pre-requisites, you will need to either get them, or as a shortcut, obtain a precompiled SQLite3 package for your OS. We have created some of these [here](https://github.com/developmentseed/node-sqlite3/issues/106).

The pre-compiled package should be downloaded, extracted and placed in the node\_modules folder, such that it lives in node\_modules/sqlite3, if you have a partial install of the SQLite3 package, replace it with the files you downloaded from github. Be sure that all the SQLite3 files and folders live directly in node\_modules/sqlite3 - there should note be a node\_modules/sqlite3/sqlite3 folder.

## Updating Ghost

Once you have a working version of Ghost up and running, updating is easy. All you need to is;

* Download the latest Ghost build
* `npm install`
* `grunt`
* `git submodule update`

Simple, 'eh?


If this however does break your Ghost application try deleting `core/shared/data/testdb.db`. ***Beware*** this **will** delete your Ghost database, **forever**, like srsly.

## Working With Ghost

When updating the SCSS and the Ghost Handlebars templates, they need to be compiled for you changes to be applied. You could do this manually, but we have done it all for you. All you need to do is run;

* `grunt watch`

This will 'watch' your working directory for changes to the SCSS and Handlebars templates, and upon you saving your changes, will automatially compile them.

## Misc. Ghost Goodies

#### Generating Docs

You can generate Ghosts Docs by running;

* `grunt docs`

This does however need [Pygments](http://pygments.org/) installed.

#### Validating Changes

If you fancy submitting some changes to the Ghost repository, you need to first check all is in order and not broken. You can do this by running;

* `grunt validate`

or individually

* `grunt jslint` < JSLints Javascript files
* `grunt test-api` < Tests API
* `grunt test-p` < Tests Permissions