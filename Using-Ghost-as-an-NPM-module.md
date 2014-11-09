You can now use Ghost as a NPM module!

### BREAKING CHANGE 

The API for using Ghost as an NPM module is changing in **0.5.2**. 

Calling `ghost()` will no longer start an express server. If you have setup Ghost this way with Ghost <0.5.2 you will need to change the code that calls the module. The new API signature is:

```
var ghost = require('ghost');
ghost().then(function (ghostServer) {
    ghostServer.start();
});
``` 

This documentation will be updated with more details closer to the release.

### Using Ghost as an NPM module

1.  Include Ghost as a dependency in your `package.json` file

  ```
"dependencies": {
      "ghost": "0.5.2"
}
  ```

2.  Run `npm install` to install Ghost.

3.  Include the Ghost module where desired and then invoke it to get a promise for a ghostServer object. 

```
var ghost = require('ghost');
ghost().then(function (ghostServer) {
    ghostServer.start();
});
``` 
At this point Ghost should be running!

## GhostServer API

The [GhostServer](https://github.com/TryGhost/Ghost/blob/master/core/server/ghost-server.js) object returned by the `ghost()` promise has the following API:

### Properties 

#### .rootApp

The base Ghost express instance which has all of Ghost's middleware and configuration mounted on it.

#### .config

Reference to the Ghost config module

### Methods
#### .start([express instance])

Starts a server listening for requests on the host & port or socket configured in `config.js`. 

* **Takes:** an optional express instance (should have Ghost mounted on it)
* **Returns:** a promise which resolves with the ghostServer instance once the server has successfully  started

#### .stop()

Stops the server

* **Returns:** a promise which resolves with the ghostServer instance once the server has successfully stopped

#### .restart()

* **Returns:** a promise which resolves with the ghostServer instance once the server has successfully restarted

## Example customizations

### Mount Ghost on a subdirectory

Ghost's default `index.js` uses this to add subdirectory support. It is possible to create a parent express instance, call `.use` to add your own middleware and configuration, and then tell the `ghostServer` to start Ghost with your new parent app.

```
var ghost = require('ghost'),
    express = require('express'),
    parentApp = express();

ghost().then(function (ghostServer) {
    parentApp.use(ghostServer.config.paths.subdir, ghostServer.rootApp);

    ghostServer.start(parentApp);
});
``` 

`ghostServer.config.paths.subdir` contains the subdirectory specified via the URL in `config.js` alternatively you can pass in any valid path string.

**Note:** If you pass in an express instance which has not had the Ghost `rootApp` mounted on it, then `ghostServer` will start a server that doesn't do anything ;)

### Decide where the `content/` directory should exist

By default Ghost will use the `content/` directory that exists inside the module.  To modify where Ghost's `content/` directory should exist you can pass in a JSON object into the `ghost()` function.  For sake of easy maintenance you can also pass in a JSON file:

  ```
ghost({
  config: path.join(__dirname, 'config.js')
});
  ```

An example `config.js` is based off the [config.example.js](https://github.com/TryGhost/Ghost/blob/master/config.example.js).

The configuration property that changes the `content/` location is:

```
paths: {
  contentPath: path.join(__dirname, 'content'),
}
```

Modify that to change where the `content/` directory should exist.

**NOTE**:  If you change the location of the `content/` directory Ghost expects to find the same directory structure that exists in the module.  To get started copy the [default content directory structure](https://github.com/TryGhost/Ghost/tree/master/content) as the basis for your custom `content/` location.