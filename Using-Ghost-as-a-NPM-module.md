*This document is still a work in progress*

There is a beta version of Ghost on NPM which can be installed via:

`npm install ghost@0.4.2-rc1`

***


Here's a simple boilerplate for using Ghost as a NPM module with the `content` folder existing outside of the npm module.

Create a new directory with the following structure:


```
content/
package.json
config.js
index.js
```


### content/

The `content/` folder is a direct copy of Ghost's content folder.  At the moment this is not created automatically for you, so for the time being you need to manually copy and paste the contents of `Ghost/content/` into the location you want.  This is required only once.

*Note:* make sure you copy over `Casper`, the default theme for Ghost.  Without Casper Ghost will not start.



### package.json

This is where you define Ghost as a npm module.

**NOTE:** Ghost is not yet published to NPM.  As a result you need to define the version as a git url.

Here's how your `dependencies` object should look:

```
"dependencies": {
    "ghost": "git://github.com/TryGhost/Ghost.git#master"
}
```


### config.js

The `config.js` file is a copy of the config.example.js file.

To set where Ghost expects the content directory to live you need to amend your `config.js` file to add an additional property.


```
production: {
  paths: {
      contentPath: path.join(__dirname, '/content/'),
  }
}
```

*Note:* Be sure to include nodejs' `path` module for the above code to work. i.e. `var path = require('path');`.


### index.js

The `index.js` is where you bootup and instantiate Ghost.

In this file you can pass where Ghost should expect the `config.js` to exist.

An example:

```
var ghost = require('ghost'),
    path  = require('path');

ghost({
  config: path.join(__dirname, 'config.js')
});
```




## Notes
Ghost requires the compilation of its assets.  This is currently not supported out of the box and requires some manual work.

Run the following in your terminal:

```
cd node_modules/ghost/
grunt production
```



After all that you should be able to run `node index.js` and Ghost should be up and running!