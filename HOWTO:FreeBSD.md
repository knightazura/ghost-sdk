# Installing Ghost on FreeBSD

Let me first of all point out that I am not a member of the Ghost project team, anything I found out may be incorrect or there may be a smarter way to do it, also I do not really use FreeBSD, this guide is everything I have done yet. If it doesn't work for you, I probably cannot help you any further.

Installing Ghost on FreeBSD should work exactly as on Linux (and on MacOS X probably), however due to some minor differences in the node.js packages, it doesn't.

The whole procedure work as of this writing (1 Feb 2014) running in VirtualBox with Ghost 0.4.1, as usual your mileage may vary. Most importantly the quirks may get fixed if the maintainers of node-sqlite3 publish a precompiled version of the package for FreeBSD or improve the build process for the source version.

I assume that you have installed FreeBSD 10.0 64 bit with the minimal setup from the install CD and are using ports to install software.

Install the following ports by doing make install as root

* www/node
* www/npm
* databases/sqlite3

As your regular user, download the ghost zip and extract it into a directory ~/ghost

Verify that both node and npm are working and have the correct version:

`$ node -v
v0.10.22`

`$ npm -v
1.3.11`

Install node-sqlite3 using the already installed sqlite libraries in /usr/local, I had to set the C++ compiler to c++ explicitly since it is using g++ which is not available. (I am planning to report this on the node-sqlite3 project, hopefully they can fix that)

`$ CXX=c++ npm install sqlite3 --sqlite=/usr/local`

Now you can install ghost with

`$ npm install --production`

and run it

`$ npm start --production`

To test the ghost blog from my host machine, I had to change the ip address from 127.0.0.1 to 0.0.0.0 to make Ghost listen on all interfaces, after that I could access the server on http://freebsd:2368/ with Firefox running on the host system.
