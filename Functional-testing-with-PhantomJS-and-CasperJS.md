This is a [nice intro](http://dannycroft.co.uk/front-end-unit-testing-with-javascript/) to functional testing with [phantomjs](http://phantomjs.org/) & [casperjs](http://casperjs.org/)

## Installation

### Mac
This is super-duper simple using [Homebrew](http://brew.sh/)

#### Phantomjs:

`brew update && brew install phantomjs`

#### Casperjs:

*Note:* Use `--devel` to get v1.1 which we require

`brew install casperjs --devel` 

###Linux / Vagrant box

#### Phantomjs:

Use `wget` to fetch the correct archive from http://phantomjs.org/download.html

E.g. for 64-bit (find out which architecture you're on with `arch`)
* $ `wget https://phantomjs.googlecode.com/files/phantomjs-1.9.8-linux-x86_64.tar.bz2`
* $ `tar xvjf phantomjs-1.9.8-linux-x86_64.tar.bz2`
* $ `cd phantomjs-1.9.8-linux-x86_64`
* $ `ln -sf "$(pwd)"/bin/phantomjs /usr/local/bin/phantomjs` (may require sudo)

#### Casperjs:

Git method is recommended. Doesn't matter where you clone casper.
* $ `git clone git://github.com/n1k0/casperjs.git`
* $ `cd casperjs`
* $ `ln -sf "$(pwd)"/bin/casperjs /usr/local/bin/casperjs` (may require sudo)

### Windows

As always, Windows is a little tricky

#### Phantomjs:

1. Download the zip from phantomjs: http://phantomjs.org/download.html
2. Unzip it to a safe/sensible location. I would recommend C:\phantomjs
3. Add `;C:\phantomjs` (or the correct path if you unzipped somewhere different) to the end of your PATH environment variable (the System one). If you're not familiar with finding your environment variables in Windows, [this should help](http://www.computerhope.com/issues/ch000549.htm).

#### Casperjs:

1\. Either:

download the latest zip from this page: http://docs.casperjs.org/en/latest/installation.html and unzip to a safe & sensible location like `C:\casperjs` 

or (**recommended**) the git method (easier to keep up to date with versions):

Via a command line (to install at `C:\casperjs`):
* `C:`
* `cd \`
* `git clone git://github.com/n1k0/casperjs.git`

or use TortoiseGIT

2\. Add `;C:\casperjs\bin` (or the correct path if you installed somewhere different) to the end of your PATH environment variable (the System one).

## Running the tests

If you want automated testing, we've got a grunt task that has you covered. The following command will have you up and running:

```
$ grunt test-functional
```

If you want to target a particular file or folder you can use:

```
$ grunt test-functional --target=client
$ grunt test-functional --target=client/app_test.js
```

The [Grunt file](https://github.com/TryGhost/Ghost/blob/master/Gruntfile.js#L750) has further documentation on this.

